# Leksione-Gjuha-JAVA
Leksionet per kursin e Gjuhes JAVA

 (int i = 0; i < n; i++) {
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
            total = total + produktet[i].vleraTotale();
        }
        System.out.println("Vlera totale e magazines: " + total + " leke");
 
        Produkti maxP = produktet[0];      // modeli i maksimumit mbi objekte
        for (int i = 1; i < produktet.length; i++) {
            if (produktet[i].vleraTotale() > maxP.vleraTotale()) {
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
