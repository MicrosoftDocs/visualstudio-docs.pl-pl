---
title: Menu i polecenia programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1f22b7ac4377b600208c079b6af1eff7fc3cbfc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698384"
---
# <a name="menus-and-commands-for-visual-studio"></a>Menu i polecenia dla programu Visual Studio
## <a name="command-usage"></a>Użycie polecenia

### <a name="overview"></a>Omówienie
 W przeciwieństwie do pakietu Microsoft Office, który jest pakietem, który składa się z wielu oddzielnych produktów, visual studio zawiera wiele produktów, które każdy przyczyniają się ich zestawy poleceń do globalnego środowiska IDE programu Visual Studio. IDE zarządza złożonością tysięcy poleceń, filtrując funkcje dostępne dla użytkownika na podstawie kontekstu.

 Gdy zmienia się kontekst użytkownika — na przykład przełączanie z okna projektu do okna edycji kodu — funkcje niezwiązane z nowym kontekstem znikają. W tym samym czasie nowe powierzchnie funkcji wraz z powiązanymi informacjami dynamicznymi, takimi jak właściwości i opcje przybornika. Użytkownik nie powinien zauważyć zamiany dostępnego zestawu poleceń. Jeśli użytkownik jest rozproszony lub zdezorientowany przez polecenia pojawiające się lub znikające, projekt interfejsu użytkownika wymaga dostosowania. Bieżący kontekst użytkownika jest zawsze wskazywany na jeden lub więcej sposobów, na przykład w pasku tytułu IDE, oknie Właściwości lub w oknie dialogowym Strony właściwości.

 Paski poleceń umożliwiają elastyczność w interfejsie użytkownika. Jedyną strukturą polecenia nieodłącznie związane ze środowiskiem programu Visual Studio są menu główne i pasek poleceń głównego, które można dostosować, a nawet ukryte. Inne paski poleceń pojawiają się i znikają na podstawie stanu aplikacji. Okna narzędzi i edytory dokumentów mogą również zawierać osadzone paski narzędzi w krawędziach okien.

#### <a name="basic-guidelines"></a>Podstawowe wskazówki

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>W miarę możliwości używaj istniejących udostępnionych poleceń, grup poleceń i menu.
 Ponieważ polecenia są zazwyczaj wyświetlane na podstawie kontekstu, użycie istniejących menu udostępnionych i grup poleceń zapewnia, że struktura poleceń pozostaje stosunkowo stabilna między zmianami w kontekście. Ponowne korzystanie z poleceń udostępnionych i umieszczanie nowych poleceń w pobliżu powiązanych poleceń udostępnionych również zmniejsza złożoność IDE i tworzy bardziej przyjazne dla użytkownika środowisko. Jeśli nowe polecenie musi zostać zdefiniowane, spróbuj umieścić go w istniejącej udostępnionej grupie poleceń. Jeśli nowa grupa musi zostać zdefiniowana, umieść ją w istniejącym menu udostępnionym w pobliżu powiązanej grupy poleceń przed utworzeniem nowego menu najwyższego poziomu.

##### <a name="do-not-create-icons-for-every-command"></a>Nie należy tworzyć ikon dla każdego polecenia.
 Zanim utworzysz ikonę polecenia, zastanów się uważnie. Ikony powinny być tworzone tylko dla poleceń, które:

- na domyślnym pasku narzędzi.

- prawdopodobnie zostaną dodane przez użytkowników do paska narzędzi za pomocą okna dialogowego **Dostosuj...**

- ikonę skojarzoną z tą samą akcją w innym produkcie firmy Microsoft.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Ograniczanie dodawania skrótów klawiaturowych
 Zdecydowana większość użytkowników zatrudnia niewielki ułamek wszystkich dostępnych skrótów. W razie wątpliwości nie należy wiązać funkcji ze skrótem klawiaturowym. Przed dodaniem nowych skrótów należy współpracować z zespołem obsługi użytkownika.

##### <a name="give-commands-a-default-menu-placement"></a>Nadaj polecenia domyślnemu umieszczeniu menu.
 Należy pamiętać, że polecenia będą dostosowywane przez innych i zaprojektować je odpowiednio. Nie ma czegoś takiego jak ukryte polecenie. Wszystkie polecenia programu Visual Studio są wyświetlane w oknie dialogowym **Narzędzia > Dostosowywanie,** Okno polecenia, automatyczne uzupełnianie, **Okno dialogowe Narzędzia > > klawiatury** oraz Środowisko narzędzi programistycznych (DTE). Upewnij się, że nadaj poleceń nazwę i etykietkę narzędzia w pliku .ctc, aby użytkownicy mogli je łatwo znaleźć.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Nie powielaj poleceń udostępnionych na osadzonym pasku narzędzi.
 Przydatne jest umieszczanie poleceń w pobliżu obszaru fokusu użytkownika. Jednym ze sposobów jest utworzenie osadzonego paska narzędzi w górnej części okna narzędzia lub edytora dokumentów. Polecenia umieszczone na pasku narzędzi powinny być specyficzne dla regionu zawartości w oknie. Nie powielaj poleceń udostępnionych na tych paskach narzędzi. Na przykład nigdy nie umieszczaj ikony "Zapisz" na osadzonym pasku narzędzi.

### <a name="content-and-command-visibility"></a>Widoczność zawartości i poleceń
 Polecenia istnieją w następujących zakresach: **Środowisko,** **Hierarchia**i **Dokument**. Znać każdy zakres, aby mieć zaufanie do umieszczania poleceń.

 Polecenia w **zakresie środowiska** ustanowić kontekst podstawowy i są współużytkowane między wieloma kontekstami. Zmieniają one widoczność lub rozmieszczenie dokumentów i okien narzędzi. Wśród poleceń w zakresie środowiska są **Nowy projekt**, **Połącz z serwerem**, **Dołącz proces**, **Wytnij**, **Kopiuj**, **Wklej**, **Znajdź**, **Opcje**, **Dostosuj**, **Nowe okno**i **Wyświetl Pomoc**.

 Polecenia w zakresie **hierarchii hierarchii** w programie Visual Studio, w tym **Project,** **Team**i **Data.** Odnoszą się one do podkontekstu projektu - na przykład **Debug**, **Build**, **Test**, **Architektura**lub **Analiza**. Wśród poleceń w zakresie hierarchii są **Dodaj nowy element,** **Nowe zapytanie,** **Ustawienia projektu,** **Dodaj nowe źródło danych,** **Kreator wydajności uruchamiania**i **nowy diagram**.

 Polecenia w zakresie **dokumentu** działają na zawartość dokumentu, takich jak kod, projekt lub kwerendy elementu pracy (WIQ). Działają one również na widok okna narzędzia lub są w inny sposób specyficzne dla tego okna narzędzia. Polecenia zakresu dokumentu działają również na obiekty plików, które same są specyficzne dla hierarchii, takie jak **Usuń z projektu**. Wśród poleceń w zakresie dokumentu znajdują **się regenerator > Rename**, **Tworzenie kopii elementu roboczego,** **Rozwiń wszystko,** **Zwiń wszystko**i **Utwórz zadanie użytkownika**.

### <a name="command-placement-decisions"></a>Decyzje dotyczące umieszczania poleceń
 Po podjęciu decyzji o utworzeniu polecenia należy określić jego odpowiednie położenie i to, czy utworzyć skrót klawiaturowy. Podążaj tą ścieżką decyzyjną, aby ustalić, gdzie umieścić polecenie:

 ![Wykres decyzji o umieszczeniu polecenia](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-a_CommandPlacement")

 **Ścieżka decyzji dla umieszczania poleceń w programie Visual Studio**

### <a name="command-placement-in-menus"></a>Rozmieszczenie polecenia w menu

#### <a name="main-menu-bar"></a>Pasek menu głównego
 Pasek menu głównego powinien być standardową lokalizacją dla poleceń dowolnych pakietów menu specyficznych dla kontekstu, które przyczyniają się do interfejsu użytkownika. Pasek menu głównego różni się od innych struktur poleceń tym, że środowisko używa go do kontrolowania, które polecenia są widoczne. Wszystkie inne paski poleceń po prostu wyłączyć polecenia, które są poza kontekstem, czy są one umieszczone w menu lub na pasku narzędzi.

 Środowisko definiuje zestaw poleceń wbudowanych w pasek menu głównego, które są wspólne dla całego IDE i wielu domen zadań. Te polecenia są zawsze widoczne, niezależnie od tego, które pakiety VSPackages są ładowane do środowiska. Chociaż VSPackages można rozszerzyć ten zestaw poleceń, zestaw poleceń z każdego produktu i rozmieszczenie ich polecenia jest odpowiedzialny za każdy zespół.

 Strukturę menu głównego programu Visual Studio można podzielić na następujące kategorie menu:

##### <a name="core-menus"></a>Menu podstawowe

- Plik

- Edytuj

- Widok

- Narzędzia

- Okno

- Pomoc

##### <a name="project-specific-menus"></a>Menu specyficzne dla projektu

- Projekt

- Kompilacja

- Debugowanie

##### <a name="context-specific-menus"></a>Menu kontekstowe

- Zespół

- Dane

- Testowanie

- Architektura

- Analiza

##### <a name="document-specific-menus"></a>Menu specyficzne dla dokumentu

- Format

- Tabela

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Podczas projektowania menu głównego należy przestrzegać następujących zasad:

- Nie przekraczaj 25 elementów najwyższego poziomu w danym kontekście

- Menu nigdy nie powinno przekraczać 600 pikseli wysokości.

- Oceń menu główne w wielu kontekstach, takich jak ultimate SKU i profil ogólny.

- Menu wysuwowe są dopuszczalne.

- Menu wysuwowe powinny zawierać co najmniej trzy elementy i nie więcej niż siedem.

- Menu wysuwane powinny przejść tylko jeden poziom głęboko — niektóre elementy menu programu Visual Studio mają podmenu kaskadowego, ale ten wzorzec nie jest zachęcany.

- Należy użyć nie więcej niż sześciu separatorów. Grupowania powinny być zgodne z następującą ilustracją:

     ![Wskazówki dotyczące grupowania menu głównego](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501-b_MainMenus")

- Chociaż nie jest wymagane, aby mieć każde grupowanie na rysunku, dodawanie dodatkowych grup jest ograniczona.

- Każda grupa powinna mieć od dwóch do siedmiu elementów menu.

#### <a name="main-menu-ordering"></a>Zamawianie menu głównego
 Przed dodaniem nowego elementu najwyższego poziomu należy rozważyć umieszczenie polecenia w istniejącym menu najwyższego poziomu. Dodając nowe menu najwyższego poziomu, należy umieścić je we właściwym miejscu. Zdecyduj, czy menu jest specyficzne dla projektu, kontekstu czy dokumentu. Zachowaj nazwę menu najwyższego poziomu zwięzłe i użyj tylko jednego słowa.

 Podstawowe menu powinny zarezerwować resztę poleceń. Plik, edycja i widok powinny być zawsze po lewej stronie, a narzędzia, okno i pomoc powinny być zawsze po prawej stronie.

#### <a name="context-menus"></a>Menu kontekstowe
 Umieszczenie zbyt dużej liczby funkcji w menu kontekstowych powoduje, że interfejs jest trudny do nauczenia się. Wszystkie główne funkcje powinny być dostępne za pośrednictwem paska menu głównego. Umieszczanie poleceń powinno być uzgadniane z istniejącymi poleceniami, aby uniknąć zduplikowanych poleceń. W przypadku menu kontekstowych powłoka definiuje standardowe grupy menu, które powinny być uwzględnione w zależności od tego, czy menu kontekstowe jest dla rozwiązania, węzła projektu lub elementu projektu.

 Podczas projektowania menu kontekstowych należy przestrzegać tych samych zasad, co w menu głównym, a ponadto:

- Nie należy przekraczać 25 elementów menu najwyższego poziomu.

- Menu wysuwania są dopuszczalne, ale nie mogą przekraczać jednego poziomu głębokości — nigdy nie należy używać kaskadowych wysuń wysuwów.

- Należy użyć nie więcej niż sześciu separatorów.

### <a name="command-placement-in-toolbars"></a>Rozmieszczenie poleceń na paskach narzędzi

#### <a name="general-toolbars"></a>Ogólne paski narzędzi
 Podczas projektowania i rozmieszczania pasków narzędzi należy przestrzegać następujących standardów:

- Nie używaj więcej niż jednego zlecenia na przycisk. Jeden przycisk = jedna akcja.

- Użyj tekstu obok ikony tylko wtedy, gdy musi być wzmocniona etykietą.

- Użyj pola kombi wyłącznie dla właściwości, które będą przełączane wiele razy w jednej sesji. W przeciwnym razie udostępnić właściwość w innym miejscu.

- Szerokość pola kombi powinna być równa szerokości najdłuższego elementu w polu + 30%. Na przykład jeśli najdłuższy element ma 200 pikseli, pole kombi powinno mieć szerokości 260 pikseli.

- Ogranicz użycie separatorów. Użycie separatora obok listy rozwijanej jest wzorcem antywzlotowym, ponieważ kształt listy rozwijanej działa jako separator wizualny.

- Grupy ikon powinny zawierać od trzech do sześciu ikon.

- Jeśli kwalifikatory powodują wiele przydatnych poleceń, użyj przycisku podziału, który przechowuje ostatnie ustawienie:

     ![Przyciski podziału w programie Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501-c_SplitButtons")

     **Przykład przycisku podziału. Sześć poleceń po lewej stronie może zmieścić się w jednym przycisku.**

#### <a name="product-specific-toolbars"></a>Paski narzędzi specyficzne dla produktu
 Każdy produkt może zapewnić domyślny pasek narzędzi, który zawiera często używane i ważne polecenia, a domyślny pasek narzędzi każdego produktu powinien pojawić się po pierwszym uruchomieniu programu Visual Studio po zainstalowaniu produktu.

 Produkty powinny również korzystać z udostępnionych grup poleceń i menu dostarczonych przez IDE. Każda udostępniona grupa poleceń jest umieszczana w menu udostępnionym przeznaczonym do organizowania powiązanych poleceń w znaczący sposób dla użytkownika. Ważne jest, aby wykorzystać tę strukturę poleceń udostępnionych w celu zmniejszenia złożoności.

#### <a name="global-toolbars"></a>Globalne paski narzędzi
 Globalne paski narzędzi muszą zmieścić się w jednym rzędzie od razu po wyjęciu z pudełka. Podczas tworzenia nowego globalnego paska narzędzi postępuj zgodnie z wytycznymi dotyczącymi tego typu paska narzędzi.

 **Ogólne wytyczne dotyczące paska narzędzi:**

- Każdy pasek narzędzi ma 24 piksele w typowych formantach (chwytak, przepełnienie).

- Każdy przycisk paska narzędzi ma 22 piksele szerokości, w tym dopełnienie. Nadanie ikonie przycisku podziału dodaje kolejne 11 pikseli szerokości.

- Duplikacja poleceń na paskach narzędzi jest dozwolona.

  **Paski narzędzi specyficzne dla dokumentu** są wyświetlane, gdy określony typ pliku jest aktywny i znikają, gdy inny typ pliku staje się aktywny.

- Paski narzędzi specyficzne dla dokumentu mogą nie mieć więcej niż 12 przycisków.

- Całkowita szerokość paska narzędzi nie może przekraczać 300 pikseli.

- Każdy typ pliku może mieć jeden osadzony pasek narzędzi lub jeden globalny pasek narzędzi specyficzny dla dokumentu, ale nie oba.

  **Paski narzędzi specyficzne dla kontekstu** są wyświetlane, gdy ustawiony jest określony kontekst i mają tendencję do pozostawanie aktywnym przez dłuższy czas.

- Limit przycisków dla wszystkich pasków narzędzi specyficznych dla kontekstu wynosi 18.

- Jeśli większość użytkowników nie będzie konsekwentnie stosować polecenia tego paska narzędzi, gdy kontekst jest aktywny, nie należy kojarzyć tego paska narzędzi z kontekstem.

- Upewnij się, że pasek narzędzi znika podczas zamykania kontekstu. Żaden z tych pasków narzędzi nie powinien pojawić się podczas uruchamiania.

  **Paski narzędzi bez kontekstu** nigdy nie pojawiają się automatycznie. Są one wyświetlane tylko wtedy, gdy użytkownik je aktywuje. Zachowaj maksymalną szerokość poniżej 200 pikseli.

### <a name="general-organization-and-shell-defined-groups"></a>Ogólna organizacja i grupy zdefiniowane w powłoki
 Użyj istniejących udostępnionych poleceń, grup poleceń i menu. Jeśli nowe polecenie musi zostać zdefiniowane, spróbuj umieścić go w istniejącej udostępnionej grupie poleceń. Jeśli nowa grupa musi zostać zdefiniowana, spróbuj umieścić ją w istniejącym menu udostępnionym w pobliżu powiązanej grupy poleceń przed utworzeniem nowego menu najwyższego poziomu. Zmniejsza to złożoność polecenia przy jednoczesnym zapewnieniu spójnego umieszczania poleceń w IDE.

 Udostępnione menu **Format,** zwykle wyświetlane w kontekście okien dokumentów w stylu projektanta, jest zilustrowane na poniższej ilustracji:

 ![Menu Format programu Visual Studio z objaśnieniami](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501-d_FormatMenu")

 **Grupy menu w programie Visual Studio**

### <a name="reducing-and-reusing-commands"></a>Zmniejszanie i ponowne odtwarzanie poleceń
 Polecenia są zazwyczaj wyświetlane na podstawie kontekstu, w celu zmniejszenia liczby poleceń, które użytkownik widzi w danym momencie. Należy jednak również ponownie użyć istniejących menu udostępnionych i grup poleceń, aby upewnić się, że struktura poleceń pozostaje stosunkowo stabilna między zmianami w kontekście.

 Ponowne korzystanie z poleceń udostępnionych i umieszczanie nowych poleceń w pobliżu powiązanych poleceń udostępnionych zmniejsza złożoność IDE i tworzy bardziej przyjazne dla użytkownika środowisko.

## <a name="naming-commands"></a>Nazywanie poleceń

### <a name="naming-conventions"></a>Konwencje nazewnictwa
 Spójne nazywanie poleceń ma kluczowe znaczenie, dzięki czemu użytkownicy mogą znajdować i wykonywać polecenia za pomocą wiersza polecenia lub powiązania ze skrótem klawiaturowym. Nazwy poleceń pomagają również użytkownikowi zrozumieć, jaki cel służy poleceniu, gdy jest wyświetlane na pasku narzędzi lub w menu kaskadowym lub kontekstowym.

#### <a name="when-naming-commands"></a>Podczas nazywania poleceń:

- Konstruuj tekst tak, aby był łatwo zlokalizowany. Aby uzyskać więcej informacji na temat lokalizowania tekstu, zobacz [Najważniejsze wskazówki dotyczące lokalizacji](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices).

- Bądź zwięzły. Polecenia powinny używać nie więcej niż trzech słów.

- Użyj wielkości litery tytułu: pierwsza litera każdego wyrazu powinna być pisana wielkich liter. Aby uzyskać więcej informacji na temat formatowania tekstu w programie Visual Studio, zobacz [Styl tekstu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

- Należy wziąć pod uwagę, gdzie zostanie umieszczone polecenie. Czy znajduje się w menu najwyższego poziomu, czy w wysuwa? Na przykład podczas grupowania poleceń wyrównania w wysunięciu wysuwu polecenie najwyższego poziomu powinno być "Wyrównaj", a polecenia wysuwania powinny być "Lewe", "Prawe", "Wyjustuj", "Usprawiedliwiaj" i tak dalej. Nazwanie poleceń wysuwania "Wyrównaj do lewej" lub "Wyrównaj do prawej" byłoby zbędne.

     ![Menu Format programu Visual Studio](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502-a_FormatMenu")

### <a name="using-icons-with-commands"></a>Używanie ikon z poleceniami
 Oszczędnie korzystać z parowania ikon z poleceniami. Chociaż skojarzenie unikatowego obrazu za pomocą polecenia przyspiesza zdolność użytkownika do identyfikowania tego polecenia, bałagan wizualny i nieefektywność występują przy nadużywaniu obrazu. Poniższe reguły pomagają przy podejmowaniu decyzji o utworzeniu ikony polecenia.

#### <a name="use-an-icon-with-a-command-only-if"></a>Ikonę z poleceniem należy używać tylko wtedy, gdy:

- To samo polecenie ma ikonę skojarzoną z nim w innym widocznym produkcie firmy Microsoft, takim jak jedna z aplikacji pakietu Microsoft Office.

- Polecenie zostanie umieszczone na domyślnym pasku narzędzi.

- Polecenie jest poleceniem specjalnym, które użytkownicy mogą dodać do paska narzędzi za pomocą okna dialogowego **"Dostosuj...".**

## <a name="access-and-shortcut-keys"></a>Klawisze dostępu i skróty

### <a name="overview"></a>Omówienie
 Istnieją dwa rodzaje przypisań klawiszy klawiatury:

- **Klawisze dostępu** (znane również jako akceleratory) umożliwiają dostęp do klawiatury za pośrednictwem menu do sterowania i każdej etykiety w interfejsie użytkownika okna dialogowego. Klucze dostępu są głównie do celów ułatwień dostępu, są przypisane do wszystkich menu i większość formantów okna dialogowego, nie są przeznaczone do zapamiętania, wpływają tylko na bieżące okno i są zlokalizowane.

- **Klawisze skrótów** używają głównie sekwencji klawiszy Control (Ctrl) i Function (Fn). Są one zaprojektowane bardziej dla zaawansowanych użytkowników i pomagają w produktywności. Są one przypisane tylko do najczęściej używanych poleceń i umożliwiają szybki dostęp, omijając menu główne. Klawisze skrótów są przeznaczone do zapamiętania i z tego powodu muszą być przypisane zgodnie ze schematem profilu. Schematy klawiszy skrótów mogą się różnić w zależności od profilu. Użytkownik może dostosować klawisze skrótów za pomocą **narzędzi > opcje > klawiatury**.

### <a name="assigning-access-keys"></a>Przypisywanie kluczy dostępu
 Klawisze dostępu składają się z klawiszy Alt plus alfanumeryczne. Przypisz klucz dostępu do każdego elementu menu bez wyjątku. Postępuj zgodnie z systemami Windows i typowymi konwencjami przypisywania kluczy dostępu. na przykład klucz dostępu do **pliku > Nowy** powinien być zawsze **Alt, F, N**.

 Nie należy używać liter o szerokości pojedynczego piksela, takich jak "i" (wielkimi lub wielkimi literami) ani małych liter "l" i unikać używania znaków z maleczami (g, j, p, q i y), ponieważ są one trudne do odróżnienia.

 Unikaj używania zduplikowanych kluczy, jeśli to możliwe. W przypadkach, gdy powielanie jest nieuniknione, system menu obsługuje konflikty przez przechodzenie przez wszystkie polecenia, które używają klucza. Na przykład dla hipotetycznego polecenia "Liczba" w menu Plik, które powiela klawisz dostępu "N", **Alt, F, N** utworzy nowy plik, a **Alt, F, N N** wykona polecenie "Number".

### <a name="assigning-shortcut-keys"></a>Przypisywanie klawiszy skrótów
 Unikaj przypisywania nowych klawiszy skrótów, ponieważ nie są one wymagane dla każdego polecenia i opodatkowania systemu (i pamięci użytkownika), jeśli są nadużywane. Dane z programu poprawy jakości obsługi klienta (CEIP) wskazują, że użytkownicy programu Visual Studio używają tylko niewielkiego podzbioru zintegrowanych skrótów.

 Podczas definiowania skrótów należy przestrzegać następujących zasad:

- **Użyj sekwencji klawiszy Control (Ctrl) i Function (Fn).**

- **Zachowaj często używane skróty.** Zachowaj najpopularniejsze skróty.

- **Łatwe wpisywać skróty do edytora.** Powiąż łatwe do wyopisania skróty do poleceń, które deweloperzy potrzebują najbardziej podczas pisania kodu. Na przykład **Edit.InvokeSmartTag** musi mieć szybki klawisz skrótu, taki jak Ctrl+/ a nie Alt+Shift+F10.

- **Dąż do konsekwentnie tematycznie skróty.**

- **Postępuj zgodnie z wytycznymi systemu Windows, aby określić, które klucze modyfikujące do zatrudnienia.** Użyj kombinacji klawiszy Ctrl dla poleceń, które mają efekty na dużą skalę, takie jak polecenia, które mają zastosowanie do całego dokumentu. Użyj kombinacji klawiszy Shift dla poleceń, które rozszerzają lub uzupełniają działania standardowego klawisza skrótu. Nie używaj kombinacji Ctrl+Alt.

- **Usuń obce skróty.** Jeśli masz starszą funkcję, rozważ usunięcie skrótów, które są używane ze skrajną częstotliwością (mniej niż 10 razy z danych programu CEIP) lub umiarkowaną częstotliwością (mniej niż 100 razy z danych programu CEIP), jeśli klucz dostępu zapewnia szybki dostęp do tego samego polecenia. Na przykład: Alt, H, C otworzy Pomoc/Zawartość.

  Nie ma prostego sposobu sprawdzania dostępności skrótów. Jeśli chcesz dodać skrót, wykonaj następujące czynności:

1. Sprawdź listę [skrótów programu Visual Studio 2013,](http://visualstudioshortcuts.com/2013/) aby ustalić, czy istnieją podobne polecenia do grupowania.

2. Przejdź do **pozycji Narzędzia > Opcje > środowisko > klawiatury** i przetestuj skrót. Sprawdź każdy schemat mapowania klawiatury wymieniony w obszarze "Zastosuj następujący dodatkowy schemat mapowania klawiatury". Sprawdź profile ogólne, c#, VB i C++, ponieważ mają unikatowe skróty. Skrót jest dostępny, jeśli nie jest mapowany w żadnym z tych miejsc.
