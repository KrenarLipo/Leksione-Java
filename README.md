# Leksione-Gjuha-JAVA
Leksionet per kursin e Gjuhes JAVA

// Online Java Compiler
// Use this editor to write, compile and run your Java code online
import java.util.Scanner;

class Produkti {
    private String emri;
    private double cmimi;
    private int sasia;
    
    public Produkti(String emri, double cmimi, int sasia){
        this.emri = emri;
        this.cmimi = cmimi;
        if(sasia >=0){
            this.sasia = sasia;
        }else{
            this.sasia = 0;
        }
    }
    
    //getters and setters
    public String getEmri(){
        return emri;
    }
    public double getCmimi() {return cmimi;}
    public int getSasia(){ return sasia;}
    
    public void setSasia(int sasia){
        if(sasia >=0){
            this.sasia = sasia;
        }
    }
    
    public double vleratTotale(){
        return cmimi*sasia;
    }
    
    public boolean kaPakStok(){
        return sasia < 5 ;
    }
    
    public void printoDetajet(){
        System.out.println(emri + " | cmimi: "+ cmimi + " |sasia: "+sasia+ " | vlera: " +vleratTotale());
    }
    
}

class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("Sa produkte do shtoni?");
        int n = sc.nextInt();
        while ( n<1||n>20){
            System.out.print("Numer i pavlershem! Jepni nga 1-20");
            n = sc.nextInt();
        }
        
        Produkti[] produktet = new Produkti[n];
        for(int i=0; i<n; i++){
             System.out.println("--- Produkti " + (i + 1) + " ---");
            sc.nextLine();                 // pastron rreshtin pas nextInt
            System.out.print("Emri: ");
            String emri = sc.nextLine();
            System.out.print("Cmimi: ");
            double cmimi = sc.nextDouble();
            System.out.print("Sasia: ");
            int sasia = sc.nextInt();
            produktet[i] = new Produkti(emri, cmimi, sasia);
        }
 
        System.out.println();
        System.out.println("=== LISTA E PRODUKTEVE ===");
        for (int i = 0; i < produktet.length; i++) {
            produktet[i].printoDetajet();
        }
 
        double total = 0;                  // modeli accumulator
        for (int i = 0; i < produktet.length; i++) {
            total = total + produktet[i].vleratTotale();
        }
        System.out.println("Vlera totale e magazines: " + total + " leke");
 
        Produkti maxP = produktet[0];      // modeli i maksimumit mbi objekte
        for (int i = 1; i < produktet.length; i++) {
            if (produktet[i].vleratTotale() > maxP.vleratTotale()) {
                maxP = produktet[i];
            }
        }
        System.out.println();
        System.out.println("=== PRODUKTI ME VLEREN ME TE LARTE ===");
        maxP.printoDetajet();
 
        int sa = 0;                        // numerimi me kusht
        for (int i = 0; i < produktet.length; i++) {
            if (produktet[i].kaPakStok()) {
                sa++;
            }
        }
        System.out.println();
        System.out.println("Produkte me pak stok (< 5): " + sa); 

    }
}
