# Witamy w finale!
Potyczki Młodych Adminów 2025

## Wstęp

Tegoroczne zadania będą testem nie tylko znajomości Kubernetes i Ranchera, ale też działania pod presją, ze szczególnym uwzględnieniem zagadnień bezpieczeństwa.

Tematem konkursu jest praca w jednej z "trzyliterowych służb" - tak tajnych, że nawet nie wymawiamy głośno tych liter. Dostaniemy trochę typowo administracyjnych zadaniań, bo przecież tajne systemy też wymagają obsługi i utrzymania - ale też zmierzymy się z działaniami agentów Rosyjskich, których aktywność będzie wymagała podjęcia odpowiednich kroków!

Powodzenia!

---
### Misja specjalna

Specjalna operacja woj... a nie, czekaj, nie mamy na to kilku lat - MISJA specjalna zostanie ogłoszona o czasie T+15minut. Obecność obowiązkowa. Misja może odmienić losy kraju - a nawet tego konkursu!

### Misja 0 - kryptonim "Red Tape"
Najlepiej napisany program i najlepiej wdrożony system jest tykającą bombą bez odpowiedniej dokumentacji. Nikt nie lubi jej pisać, ale jest kluczowa dla łatwości późniejszego utrzymywania i efektywnej współpracy - a także do sprawdzania zadań! Dlatego udokumentuj wszystkie zadania, co najmniej oznaczając te które zostały wykonane, bo **tylko te zostaną sprawdzone**. Niektóre zadania wymagają pisemnej odpowiedzi, umieść je też w dokumentacji. Zalecany - nie, JEDYNIE SŁUSZNY - sposób na przedstawienie dokumentacji to utworzenie repozytorium GitHub (polecam utworzenie forka tego repo).

Opisz kroki wykonane w celu realizacji zadania, szczególnie lokalizacje zasobów, użyte opcje i komendy - nie musisz tego robić bardzo dokładnie, ale w razie wątpliwości będą one działać na twoją korzyść. Na przykład jeśli zadanie nie zostało do końca wykonane, ale znacząca część kroków jest opisana poprawnie, zaliczę za to częściowe punkty. Albo jeśli zadanie zostało wykonane, ale nie w sposób jakiego oczekiwałem, to opis będzie kluczem do uzyskania za nie punktów. To, co nie jest opisane, a nie jest oczywiste z interfejsu Ranchera, będzie rozstrzygane na twoją niekorzyść!

### Misja 1 - operacja "Otwarte Okno"
Potrzebujemy nowego serwera webowego do ogłaszania krytycznych informacji ze Sztabu Zarządzania Kryzysowego, ale minister cały dzień jadł ośmiorniczki i dlatego dopiero teraz dotarły rozkazy. Wszyscy inni poszli już do domu, więc cała nadzieja w waszym zespole.
Na klastrze "potyczki" utwórz projekt "szk-server" a w nim namespace "ogloszenia-krytyczne". W tym namespace uruchom serwer webowy. Nie mówią jaki, więc użyj dowolnego, ale ma być w najnowszej wersji. **3pkt**
- Utwórz usługę dzieki której można się odwołać do naszego serwera z całego klastra **3pkt**
- Instrukcje mówią o wysokiej dostępności tej usługi - nie masz dostępu do większej liczby maszyn, więc zrób co się da, żeby zwiększyć jej dostępność w obrębie istniejących zasobów **3pkt**
- Zapewnij dostępność usługi na internet. Nie masz czasu czekać do jutra aż administratorzy sieci udostępnią ci firmowy DNS, a potrzebujesz szybko przetestować dostępność, więc wymyśl jak zapewnić rozwiązywalny url wskazujący na IP hosta, na którym jest twój klaster "potyczki". **20pkt** (pełnym sukcesem operacji jest podanie adresu rozwiązywalnego przy pomocy publicznego DNS z internetu, pod którym zgłosi się działająca strona internetowa);

### Misja 2 - kryptonim "Long Horn"
Potrzebujemy Persistent Storage, szybko! Tylko musi być taki, żeby umożliwiał replikację! Wprawdzie i tak mamy tylko jeden serwer w klastrze, więc musimy ograniczyć liczbę replik do 1, ale sama obsługa replikacji jest ważna dla morale dowództwa - nieważne, że działa tylko na papierze... Nfs provisioner jest wykluczony, potrzebne jest coś lepszego. Gdyby tylko w Rancherze istniało jakieś repozytorium z łatwym w instalacji i obsłudze rozwiązaniem storage dla Kubernetes...
Zainstaluj rozwiązanie typu software-defined storage w najnowszej stabilnej wersji na klastrze "potyczki", ustawiając w konfiguracji instalacyjnej 1 replikę i domyślny StorageClass. **5pkt**
Sukces misji oznacza działającą aplikację storage oraz dostępną StorageClass.

### Misja 3 - operacja "Koci Pazur"
Kot prezesa się nudzi, należy mu zapewnić jakąś rozrywkę.
Dodaj nowe repozytorium do katalogu aplikacji Ranchera. URL repo: https://rancher.github.io/rodeo **5pkt**

Zainstaluj dowolną grę z nowo dodanego repo. **5 pkt**

### Misja 4 - kryptonim "Armor Plate"
Musimy wzmocnić nasze zabezpieczenia dedykowanymi rozwiązaniami security! Same firewalle to za mało w erze Kubernetes. Potrzebujemy najwyższej klasy ochrony - takiej jaka jest stosowana przez amerykańskie trzyliterowe służby.

Z katalogu aplikacji zainstaluj NeuVector w najnowszej stabilnej wersji. **5pkt**

Włącz funkcję Auto-scan **1 pkt**

Zbadaj czy istnieją podatności dla wersji Kubernetes uruchomionej na klastrze potyczki - podaj ich liczbę i jeśli nie jest równa zero, podnieś wersję Kubernetes klastra potyczki do 1.26. **5pkt**

### Misja 5 - operacja Czyste Ręce
Wdrożenie AI byłoby niesłychanie użyteczne w naszych zadaniach, idealnie byłoby zacząć od narzędzia Ollama. Ale trzeba  się upewnić, że te obrazy nie zawierają podatności - najpierw musimy je przeskanować! 
Użyj NeuVector, żeby przeskanować repozytorium Ollama z rejestru https://registry.hub.docker.com ; jako rozwiązanie podaj nazwę image z największą ilością podatności, oraz liczbę tych podatności. **7pkt**

### Misja 6 - kryptonim Zero Zaufania
Nasz system wczesnego ostrzegania wykrył podejrzaną aktywność, którą przechwycilismy. Wdróż na klastrze zinfiltrowany zasób w odpowiednim namespace (podejrzany-agent.yaml). Natychmiast odetnij wszelką komunikację sieciową (przychodzącą i wychodzącą) z/do tego poda, żebyśmy mogli go szczegółowo przeanalizować. **10pkt**
Przetestuj działanie zabezpieczeń dla połączeń przychodzących i wychodzących z podejrzanego poda. Załącz do odpowiedzi odpowiednie Security Violations z NeuVectora pokazujące zablokowaną próbę naruszenia blokady.**5pkt**
Utwórz pomocniczego poda nginx o nazwie detektor w namespace kwarantanna. Zmień reguły zabezpieczeń podejrzanego poda, tak, aby dopuszczały połączenie do poda detektor. Wygeneruj ruch sieciowy z podejrzanego-agenta do detektora (cokolwiek, może być ping). Użyj NeuVector aby dokonać przechwycenia pakietów z tej komunikacji. **10pkt**
Dokonaj "analizy" przechwyconego pakietu (znajdź odpowiednie narzędzie) - skopiuj pola opisujące jeden z pakietów: źródłowe i docelowe IP, protokół, długość, info. **5pkt**

### Misja 7 - kryptonim Enigma Reactivation
Dzięki owocnej współpracy z wywiadami innych krajów NATO pomyślnie przechwyciliśmy zaszyfrowaną rosyjską transmisję. Niestety moduł deszyfrujący uległ awarii - po krótkim śledztwie okazało się, że tym razem to nie działanie wroga, ale zwyczajna niekompetecja - ktoś bardzo mądrze użył AI do wygenerowania konfiguracji i zastąpił wszystkie istniejące kopie. Przeanalizuj i napraw deszyfrator-pod-uszkodzony.yaml - bez niego przechwycona transmisja jest bezużyteczna!
Misja zakończona powodzeniem jesli pod deszyfrator przedzie w stan Completed, a w jego logach pojawi się odszyfrowana wiadomość ()

### Zadanie 7.5
Adrian uruchomił aplikację składającą się z front-endu i bazy danych MySQL. Widzisz, że jego kontener MySQL jest uruchomiony na najprostszych domyślnych ustawieniach. Czy jest to zalecany sposób? Uzasadnij w kilku zdaniach (min. 20 słów dla pełnej punktacji).
**5pkt**, +**5pkt** jeśli uzasadnienie zawiera za i przeciw oraz sugestię poprawy

### Zadanie 8
Wytłumacz Adrianowi w kilku prostych zdaniach czym jest resource o nazwie Gateway w Kubernetes? (min. 20 słów dla pełnej punktacji)
**7pkt**

### Zadanie 9
Adrian jest bardzo skonfundowany dlaczego są dwa różne resource w Kubernetes, które "robią to samo" czyli zarządzają zestawem identycznych podów: Deployment i ReplicaSet. Wyjaśnij mu na czym polega różnica między tymi resource'ami. (min. 20 słów dla pełnej punktacji)
**7pkt**

### Zadanie 10
Dokonaj aktualizacji klastra "potyczki" to nowszej wersji Kubernetes tak, żeby zminimalizować jej wpływ na dostępność uruchomionych workloadów. **10pkt**

### Zadanie 11
Firma zatrudniła właśnie dwóch nowych pracowników, jako administrator środowiska Kubernetes twoim zadaniem jest utworzyć dla nich konta użytkowników o nazwach w formacie imie.nazwisko i poprawnie przypisać im uprawnienia:
- Nowym dyrektorem IT został Muhammed Yassuff i nalega, żeby mieć podgląd na działanie całego środowiska (uprawnienia get, list, watch).
- Przyjęliśmy także świeżego praktykanta, któremu na razie powierzyliśmy tylko utrzymanie (tj. pełna kontrola) projektu "web-server". Nazywa się on Muhhamad Yussuff.

**5 pkt** za utworzenie dwóch lokalnych użytkowników, po **7 pkt** za poprawne przypisanie uprawnień do każdego z nich (**+5** dodatkowych punktów za rozwiązanie bez żadnej pomyłki i nie nadanie dyrektorowi prawa do podglądu sekretów)

### Zadanie 12
Jeden z workloadów na klastrze "potyczki", Deployment o nazwie "mysql", nie działa poprawnie. Deweloperzy napisali yaml, ale winią Adriana bo on go zdeployował na klastrze i na pewno coś popsuł bo yaml przecież był ok. Znajdź przyczynę błędu i napraw go. **30 pkt**

### Zadanie 13
Nasz workload "nginx" z projektu "web-server" (Zadanie 1) jest prawdopodobnie atakowany z internetu! Użyj NeuVector, żeby zwizualizować wszystkie połączenia sieciowe w klastrze i zapisz zrzut ekranu do dokumentacji (**5 pkt**), oraz przechwyć i zapisz pakiety z ruchu przychodzącego do "nginx" (**10 pkt**). Jeśli Zadanie 1 jest niewykonane, możesz przechwycić pakiety innego poda (udokumentuj który). Możesz sztucznie wygenerować zapytania, żeby mieć co przechwycić.

+**7 pkt** za opis na czym polega analiza pakietów i podanie przykładowego narzędzia do takiej analizy (min. 20 słów dla pełnej punktacji)

### Zadanie 14
Adrian próbuje zdeployować nowy workload i chyba tym razem rzeczywiście coś zepsuł bo za nic nie chce się to uruchomić. Napraw i uruchom adrian-nginx.yaml w nowym namespace o nazwie "adrian". **40 pkt**

### Zadanie 15
Przy pomocy NeuVector utwórz regułę blokującą połączenia wychodzące z nginx (Zadanie 1) na zewnątrz klastra i przełącz w tryb aktywnej ochrony (Protect). (**10 pkt**) Wyeksportuj regułę jako CRD w trybie Protect i załącz do dokumentacji (**5 pkt**). Potwierdź działanie reguły logując się do shella poda nginx i wykonując polecenie curl suse.com  (**7 pkt**). Zablokuj również samo polecenie curl w tym podzie i potwierdź działanie reguły logując się do shella. (**10 pkt**). Dopuszczalne potwierdzenia to zrzuty ekranu lub skopiowane w całości komunikaty shella wraz z poleceniem, które je wyzwoliło - dołącz do dokumentacji.

### Zadanie 16
Jedna z naszych Service nie może się połączyć ze wskazanym Deployment'em. Uruchom "serwis.yaml" w nowym namespace "serwis" i napraw przyczynę problemu. Rozwiązaniem jest Service wskazujący poprawnie na Pod'a nginx zdeployowanego przez "serwis.yaml". **35 pkt**

### Zadanie 17
Kolejna instancja mysql sprawia problemy, Adrian od trzech dni przez nią nie śpi bo trzyma klaster i przecież wszystko sprawdził. Uruchom baza.yaml w nowym namespace "baza" i doprowadź do poprawnego załadowania się bazy danych. **25 pkt**

### Zadanie 18
Adrian chciał uruchomić aplikację "hello-world", ale nawet to mu nie działa. Znajdź przyczynę problemu i uruchom hello-world. **20 pkt**

