# Leksione-Gjuha-JAVA
Leksionet per kursin e Gjuhes JAVA

//Ushtrimi i 2 me shume klasa
// Online Java Compiler
// Use this editor to write, compile and run your Java code online
import java.util.ArrayList;
import java.util.Scanner;

class Anetari {
    private String emri;
    private int mosha;
    
    public Anetari(String emri, int mosha){
        this.emri = emri;
        this.mosha = mosha;
    }
    
    public String getEmri(){
        return emri;
    }
    
    public int getMosha() { return mosha; }
    
    public void prezantohu(){
        System.out.println("Jam "+emri+", " + mosha + " vjec");
    }
    

}

class Studenti extends Anetari {
    private String fakulteti;
    
    public Studenti(String emri, int mosha, String fakulteti){
        super(emri,mosha);
        this.fakulteti = fakulteti;
    }
    
    public void prezantohu(){
        super.prezantohu();
        System.out.println(" Student ne Fakultetin: "+fakulteti);
    }
    
    //Pjesa qe shtova ne klase
    public void prezantohu(int nr){
        System.out.println("Numri: "+nr);
    }
}

class Pedagogu extends Anetari {
    private String lenda;
    public Pedagogu(String emri, int mosha, String lenda){
        super(emri,mosha);
        this.lenda = lenda;
    }
    
    @Override
    public void prezantohu(){
        super.prezantohu();
        System.out.println(" Pedagogu i lendes:  "+lenda);
    }
}



class Main {
    public static void main(String[] args) {
        System.out.println("Start small. Ship something.");
        
        Scanner sc = new Scanner(System.in);
        ArrayList<Anetari> anetaret = new ArrayList<>();
        
        //Perdorimi i polimorfizmit qe nuk ju tregova ne klase
        Studenti st = new Studenti("Toni",34,"RRR");
        st.prezantohu(5);
        //Pra prezantohu e kemi perdour 3 here
        
        System.out.println("Shtoni anetaret derisa te shkruhet 'fund' per te mbyllyr regjistrimin");
        
        while(true){
            System.out.print("Shto Emrin: ");
            String emri = sc.nextLine();
            if(emri.equals("fund")){
                break;
            }
            System.out.print("Jepni moshen: ");
            int mosha = sc.nextInt();
            sc.nextLine();
            
            System.out.print("Tipi (1 = Student, 2 = Pedagog): ");
            int tipi = sc.nextInt();
            sc.nextLine();
            
            if(tipi == 1){
                System.out.print("Fakulteti: ");
                String fakulteti = sc.nextLine();
                anetaret.add(new Studenti(emri,mosha,fakulteti));
            }else{
                 System.out.print("Lenda: ");
                String lenda = sc.nextLine();
                anetaret.add(new Pedagogu(emri,mosha,lenda));
            }
            
        }
        System.out.println();
        System.out.println("===== Te gjithe anetaret ("+anetaret.size()+") =====");
        //shfaqja e listes se anetareve
        for(int i=0; i< anetaret.size(); i++){
            anetaret.get(i).prezantohu();
        }
        
        int moshaTotale = 0;
        for(int i=0; i<anetaret.size(); i++){
            moshaTotale = moshaTotale + anetaret.get(i).getMosha();
        }
        
        
        
        if(anetaret.size()>0){
            double mesatarja = (double) moshaTotale/anetaret.size();
            System.out.println();
            System.out.println ("Mesatarja: " + mesatarja+ "*");
            
            Anetari meVjetri = anetaret.get(0);
            for(int i = 1; i<anetaret.size(); i++){
                if(anetaret.get(i).getMosha() > meVjetri.getMosha()){
                    meVjetri = anetaret.get(i);
                }
            }
            System.out.println("Anetari me i vjeter eshte: ");
            meVjetri.prezantohu();
        }
        
       // System.out.println("Mosha totale: "+moshaTotale);
        
    }
}

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
