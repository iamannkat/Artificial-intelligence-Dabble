# Artificial-Intelegence-Exersises
First Dabble in A.I.

The first part - sphere a
Σχετικά με την πρώτη εργαστηριακή άσκηση, προκειμένου να κατασκευάσουμε το πρόγραμμα αναζήτησης για την επίλυση του ζητούμενου προβλήματος σφαιρών, έχουμε 
υλοποιήσει τα εξής (οι παρακάτω συναρτήσεις και δομές αναλύονται με την σειρά που εμφανίζονται στον κώδικα μας):
> Αρχικά, στο class node κρατάμε πληροφορίες που αφορούν τον κάθε κόμβο του δέντρου.
> Δημιουργούμε έπειτα ArrayList ονόματος tree, προκειμένου να κατασκευάσουμε το δέντρο και ένα ArrayList, ονόματος results, ώστε να 
παρουσιάζουμε τα αποτελέσματα στον χρήστη.
> Στη συνέχεια, έχουμε δημιουργήσει μια συνάρτηση found_solution, η οποία θα ελέγχει αν κάθε τρέχουσα κατάσταση πληροί τα κριτήρια του 
προβλήματος, προκειμένου να δούμε αν η κατάσταση αυτή είναι αποδεκτή λύση.
> Έπειτα, κατασκευάσαμε μια συνάρτηση find_children η οποία παίρνοντας σαν όρισμα μια τρέχουσα κατάσταση, βρίσκει όλες τις πιθανές εναλλαγές
θέσεων των σφαιρών.
> Ακολούθως, έγινε υλοποίηση μιας συνάρτησης search_if_exists η οποία καλείται στην find_children, για να επιβεβαιώσουμε ότι δεν θα πάρουμε
την ίδια κατάσταση δύο φόρες, γεγονός που μπορεί να προκύψει από διαφορετικές μεταθέσεις σφαιρών.
Επειδή ξεκινάμε με συγκεκριμένη κατάσταση εισόδου και προχωράμε με βάση το μικρότερο κόστος, αυτή η ίδια κατάσταση που δεν θα προστεθεί, δεν μπορεί να
προκύψει με μικρότερο κόστος σε σχέση με τη ήδη υπάρχουσα.
> Τέλος, στη συνάρτηση ucs, ξεκινάμε διατρέχοντας το ArrayList του δέντρου (που αρχικά έχει μέγεθος 1, λόγω του root που έχει γίνει add από τη συνάρτηση init) και
ελέγχουμε κάποιες συνθήκες για να δούμε αν έχουμε επισκεφθεί ξανά αυτόν τον κόμβο ή αν πρόκειται για λύση. Εφ’όσον δεν αποτελεί λύση, καλούμε την find_children για
να προσθέσει στο δέντρο όλες τις μεταβάσεις που προκύπτουν από τον τρέχοντα κόμβο, έτσι ώστε η ucs που καλείται αναδρομικά αμέσως μετά, να έχει καινούριους κόμβους 
στο δένδρο προς διερεύνηση. Πρακτικά, η τερματική συνθήκη της αναδρομής, είναι το αποτέλεσμα της found_solution η οποία και όταν γίνει true, με κλήση της συνάρτηση 
show_result θα τυπώσει και το αποτέλεσμα.

The second part - sphere b

Το δευτέρο μέρος της πρώτης άσκησης, είναι όμοιο με το πρώτο, με μόνη και κύρια διαφορά να αποτελεί ο αλγόριθμος αναζήτης Α*, αντί του UCS 
που χρησιμοποιήθηκε προηγουμένως.
Ο αλγόριθμος Α*, χρησιμοποιεί μια ευρετική συνάρτηση h(n).
Επεξήγηση Ευρετικής Συνάρτησης h(n):
Πιο συγκεκριμένα, παρατηρώντας τις κινήσεις των σφαιριδίων μέχρι να φτάσουν σε τελική κατάσταση, επινοήσαμε μια συνάρτηση h(n), η οποία 
δίνει μια εκτίμηση από την πλησιέστερη τερματική κατάσταση. Ο τρόπος λειτουργίας της συνάρτησης, είναι ο εξής:
-Καθώς διατρέχουμε το input μας, έχουμε ορίσει counters οι οποίοι μετρούν τον αριθμό εμφάνισης μαύρων και άσπρων σφαιριδίων.
- Όταν ο αριθμός των μαύρων σφαιριδίων ισούται με τον αριθμό n (όπου n ο αριθμός λευκών και μαύρων σφαιριδίων που ζητά η εκφώνηση, αντίστοιχα), δηλαδή όταν συναντήσουμε την τελευταία μαύρη σφαίρα, τότε παίρνουμε τον counter των λευκών σφαιριδίων εκείνη την στιγμή
-Γνωρίζοντας λοιπόν, πόσες λευκές σφαίρες υπάρχουν πριν την τελευταία μαύρη σφαίρα, πολλαπλασιάζουμε τον αριθμό αυτόν των λευκών σφαιρών με τον αριθμό n που έχουμε δώσει ως input στο πρόγραμμα μας.
-Ο αριθμός αυτός, θα είναι πάντα μικρότερος ή ίσος του πραγματικού κόστους από την τελική κατάσταση, συνεπώς σε κάθε περίπτωση θα ισχύει ότι h(n) <= a(n), (όπου a(n) πραγματικό κόστος).
Τελικά, αφού ισχύει h(n) <= a(n) για κάθε n, η ευρετική συνάρτηση είναι αποδεκτή και έτσι, ο αλγόριθμος Α* είναι πλήρης και βέλτιστος.\

the third part - SOS game

Σκοπός της δεύτερης άσκησης είναι να υλοποιήσουμε το παιχνίδι SOS. Ακολουθεί η περιγραφή των δομών και συναρτήσεων 
που κατασκευάσαμε, με την σειρά εμφανίζονται στον κώδικά μας.
 Αρχικά, στην class Move κρατάμε πληροφορίες για την κίνηση του παίκτη και στην class Node πληροφορίες για τις πιθανές καταστάσεις του board και άλλων
δομών που θα χρησιμοποιήσουμε παρακάτω (πχ ArrayList children που περιέχει τις καταστάσεις που μπορούν να προκύψουν από την τρέχουσα κατάσταση, Boolean player
που μας δείχνει ποιος παίκτης έχει σειρά σε κάθε κατάσταση, Node nextMove που είναι ένα πεδίο που ενημερώνουμε καθώς συγκρίνουμε τα κόστη στην συνάρτηση minimax 
για να βρίσκουμε την επόμενη κίνηση πιο εύκολα κλπ)
 Στη συνέχεια, ορίζουμε την συνάρτηση isMoveLeft, που ελέγχει αν έχει γεμίσει ο πίνακας board και δεν υπάρχουν διαθέσιμες κινήσεις.
 Ακολουθεί η συνάρτηση evaluate, στην οποία ελέγχουμε αν έχει σχηματιστεί SOS στον πίνακα και επιστρέφει 1 αν έχει σχηματιστεί, διαφορετικά επιστρέφει 0.
 Έπειτα υλοποιούμε την συνάρτηση DFS, η οποία αναπτύσσει πλήρως το δένδρο του παιγνίου, βάζοντας στα φύλλα του τα κόστη των πιθανών τελικών καταστάσεων.
Στις τελικές αυτές καταστάσεις, αν σχηματίζεται SOS που προκύπτει από κίνηση του υπολογιστή το κόστος είναι +1, διαφορετικά αν προκύπτει από κίνηση του παίκτη τότε
είναι -1. Αν πάλι, γεμίσει ο πίνακας χωρίς να δημιουργηθεί SOS, τότε το κόστος είναι 0 και έχουμε ισοπαλία.
 Στη συνέχεια, κατασκευάσαμε την συνάρτηση minimax ώστε να διατρέχει το δέντρο αναδρομικά από τα φύλλα προς τη ρίζα, συγκρίνοντας τα κόστη και ενημερώνοντάς τα, 
ενημερώνοντας επίσης και το πεδίο nextMove του κάθε κόμβου.
Τέλος, μέσα σε μια while-loop, υλοποιείται το παιχνίδι. Η κίνηση του υπολογιστή, είναι να μεταβεί από την τρέχουσα 
κατάσταση στην επόμενη, χρησιμοποιώντας το πεδίο nextMove. Έπειτα, χρησιμοποιώντας το πεδίο board του κόμβου nextMove, ενημερώνουμε
το board. Με τη σειρά του ο παίκτης, εισάγει τα στοιχεία της κίνησής του, βάση των οποίων αλλάζει και το board, και καλώντας την findcur, ενημερώνουμε 
τον κόμβο στον οποίο έχει μεταφερθεί ο υπολογιστής για την επόμενή του κίνηση. Η διαδικασία αυτή, επαναλαμβάνεται μέχρι να τερματίσει το παιχνίδι.
 Ακολουθεί η συνάρτηση printBoard, η οποία θα τυπώσει τον πίνακα μας και η printTree που απλά για δική μας διευκόλυνση κατά την εκσφαλμάτωση του κώδικα, τυπώνει 
το δέντρο.
 Σημαντική είναι και η συνάτηση findcur που χρησιμοποιούμε αμέσως μετά, η οποία παίρνοντας ως ορίσματα ένα node και ένα board, μας επιστρέφει σε ποιο από τα
παιδιά αυτού του node αντιστοιχεί αυτό το board. Χρησιμοποιείται, ουσιαστικά, για να χρησιμοποιήσει την πληροφορία της κίνησης του παίκτη προκειμένου 
να ενημερώσει τον υπολογιστή για τον κόμβο που θα βρεθεί στην επόμενή του κίνηση.
 Τέλος στη main, αρχικά καλούνται οι DFS και minimax για δημιουργία και ενημέρωση του δένδρου παιγνίου. Έπειτα, μια μεταβλητή char 
αρχικοποιείται στη ρίζα του δέντρου και θα χρησιμοποιηθεί παρακάτω για την τρέχουσα κατάσταση του παιχνιδιού και μια μεταβλητή board
που αποθηκεύει τον πίνακα. Πάνω σ’αυτόν τον πίνακα, θα αποθηκεύονται οι αλλαγές που προκύπτουν ως αποτέλεσμα της κίνησης του κάθε παίκτη.