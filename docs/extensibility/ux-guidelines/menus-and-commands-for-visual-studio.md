---
title: Menu i poleceń dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1b726d13d77c56446ff19dbb477d29ec58627341
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690633"
---
# <a name="menus-and-commands-for-visual-studio"></a>Menu i poleceń dla programu Visual Studio
## <a name="command-usage"></a>Użycie polecenia

### <a name="overview"></a>Omówienie
 W odróżnieniu od Microsoft Office, który jest mechanizm, który składa się z wielu oddzielnych produktów, program Visual Studio zawiera wiele produktów każdego przyczyniają się ich zestawy poleceń globalne środowiska IDE Visual Studio. IDE zarządza złożoność tysiące poleceń, filtrując funkcji dostępnych dla użytkowników na podstawie kontekstu.

 Podczas zmiany kontekstu użytkownika — np. przełączanie z okna projektu do okna na edytowanie kodu — funkcjonalność niezwiązanych ze sobą na nowy kontekst zniknie. W tym samym czasie nowe powierzchnie funkcji wraz z powiązanych informacji dynamicznych, takich jak opcje właściwości i przybornika. Użytkownik nie zauważy, zamiana zestawu dostępnych poleceń. Jeśli użytkownik jest efektów lub mylić za pomocą poleceń, pojawiają się lub zniknął, projekt interfejsu użytkownika wymaga dostosowania. Bieżący kontekst użytkownika jest zawsze wskazywany w jeden lub więcej sposobów, takich jak w pasku tytułu środowiska IDE, w oknie właściwości lub okno dialogowe strony właściwości.

 Paski poleceń umożliwiają elastyczne w interfejsie użytkownika. Tylko polecenia konstrukcje nieprzerwaną pracę w programie Visual Studio, środowiska są główne menu i paska poleceń główne, które zarówno można dostosowywać i nawet ukryte. Inne paski poleceń pojawiają się i znikają zależności od stanu aplikacji. Okna narzędzi i edytory dokumentu może również zawierać osadzonych paski narzędzi w ramach ich krawędzi okna.

#### <a name="basic-guidelines"></a>Podstawowe wytyczne

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Użyj istniejących udostępnionych poleceń, grup poleceń i menu, jeśli to możliwe.
 Ponieważ polecenia są zwykle wyświetlane w oparciu o kontekście, korzystanie z istniejącymi menu udostępnionych i grup poleceń gwarantuje, że strukturę polecenia pozostaje względnie stałym poziomie między zmianami w kontekście. Ponowne użycie udostępnionych poleceń i wprowadzania nowych poleceń blisko powiązane polecenia udostępnionego także zmniejsza złożoność środowiska IDE i tworzy użytkownikom większy komfort pracy. Jeśli nowego polecenia musi być zdefiniowana, spróbuj umieścić go w istniejącej grupie udostępnionego polecenia. Jeśli nowa grupa musi być zdefiniowana, umieść go w istniejącego menu udostępnionego blisko grupą powiązanych poleceń, przed utworzeniem nowego menu najwyższego poziomu.

##### <a name="do-not-create-icons-for-every-command"></a>Nie należy tworzyć ikony dla każdego polecenia.
 Zastanów się przed utworzeniem ikona polecenia. Ikony, należy utworzyć tylko w przypadku polecenia który:

-   są wyświetlane na pasku narzędzi domyślne.

-   mogą zostać dodane przez użytkowników do narzędzi za pośrednictwem **Dostosuj...**  okna dialogowego.

-   zawiera ikony skojarzone z tego samego działania w innego produktu firmy Microsoft.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Limit dodawania skróty klawiaturowe
 Większość użytkowników, zastosować niewielki ułamek wszystkie dostępne skróty klawiaturowe. W razie wątpliwości, nie należy powiązać Twojej funkcji skrótu klawiaturowego. Praca z użytkownika środowisko zespołu przed dodaniem nowych skrótów.

##### <a name="give-commands-a-default-menu-placement"></a>Nadaj polecenia domyślne położenie menu.
 Należy pamiętać, że poleceń zostaną dostosowane przez inne osoby i projektować je odpowiednio. Brak coś takiego jak ukryte polecenia. Wszystkie polecenia programu Visual Studio są wyświetlane w **Narzędzia > Dostosuj** okno dialogowe, w oknie wiersza polecenia, automatycznego uzupełniania **Narzędzia > Opcje > klawiatury** okien dialogowych i środowiska narzędzi rozwoju (DTE). Upewnij się zapewnić poleceń, nazwy i etykietki narzędzi w pliku .ctc tak, aby użytkownicy je łatwo odnaleźć.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Nie zduplikowane udostępnionych poleceń na osadzonym pasku narzędzi.
 Jest to przydatne do polecenia należy umieścić w pobliżu obszar koncentracji uwagi użytkownika. Jednym ze sposobów, w tym celu jest tworzenie osadzonym pasku narzędzi u góry okna narzędzi lub dokumentu edytora. Polecenia umieszczone na pasku narzędzi powinny być specyficzne dla regionu zawartości w oknie. Nie zduplikowane udostępnionych poleceń na te paski narzędzi. Na przykład nigdy nie należy umieścić "Zapisz" w osadzonym pasku narzędzi.

### <a name="content-and-command-visibility"></a>Widoczność zawartości i polecenia
 Istnieją polecenia w następujących zakresów: **Środowisko**, **hierarchii**, i **dokumentu**. Znać każdego zakresu, aby mieć pewność, w położenie polecenia.

 Polecenia w **środowiska** zakresu ustanowić kontekst podstawowy i są współużytkowane w wielu kontekstach. Zmieniają widoczność lub układ dokumentów i okien narzędzi. Wśród poleceń w środowisku są zakresu **nowy projekt**, **Połącz z serwerem**, **dołączanie procesu**, **Wytnij**,  **Kopiuj**, **Wklej**, **znaleźć**, **opcje**, **dostosować**, **nowe okno**, i **Wyświetl Pomoc**.

 Polecenia w **hierarchii** zakresie zarządzanie hierarchiami w programie Visual Studio, w tym **projektu**, **zespołu**, i **danych**. Dotyczą one kontekst podrzędny projektu — na przykład **debugowania**, **kompilacji**, **testu**, **architektury**, lub **analizy** . Wśród poleceń w hierarchii są zakresu **Dodaj nowy element**, **nowe zapytanie**, **ustawienia projektu**, **Dodaj nowe źródło danych**, **Uruchom Kreatora wydajności**, i **nowy Diagram**.

 Polecenia w **dokumentu** zakres działanie na nich zawartość dokumentu, takie jak kod, projekt lub kwerendy elementu roboczego (WIQ). Również działać w widoku okna narzędzi lub w przeciwnym razie są specyficzne dla tego okna narzędzia. Polecenia zakresu w dokumencie również względem obiektów plików, które znajdują się w hierarchii specyficzne dla, takie jak **Usuń z projektu**. Wśród poleceń w dokumencie są zakresu **Refaktoryzuj > Zmień nazwę**, **Utwórz kopię elementu roboczego**, **Rozwiń wszystko**, **Zwiń wszystko**, i **Utwórz zadanie użytkownika**.

### <a name="command-placement-decisions"></a>Decyzje dotyczące umieszczania poleceń
 Po podjęciu utworzyć polecenie, należy określić jego położenie odpowiednie i czy chcesz utworzyć skrót. Wykonaj tę ścieżkę decyzja do ustanowienia gdzie umieścić polecenia:

 ![Wykres decyzji — polecenie umieszczania](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501 a_CommandPlacement")

 **Decyzja ścieżkę położenie polecenia w programie Visual Studio**

### <a name="command-placement-in-menus"></a>Położenie polecenia w menu

#### <a name="main-menu-bar"></a>Główny pasek menu
 Na pasku menu głównego należy standardowej lokalizacji dla poleceń wszelkie pakiety menu kontekstowych, które przyczyniają się do interfejsu użytkownika. Na pasku menu głównego różni się od innych struktur polecenia, w tym środowisku używa ich do kontrolki, w której polecenia są widoczne. Wszystkie paski poleceń po prostu wyłącz polecenia, które są poza kontekstem, czy zostały one umieszczone w menu lub paska narzędzi.

 Środowisko definiuje zestaw poleceń oparta na pasku menu głównego, które są wspólne dla wielu domen zadań i całego środowiska IDE. Te polecenia są zawsze widoczne bez względu na to kolekcja pakietów VSPackage są ładowane do środowiska. Mimo że pakietów VSPackage można rozszerzyć ten zbiór poleceń, zestaw z każdego produktu i umieszczania ich poleceń poleceń odpowiada każdego zespołu.

 Struktura głównego menu programu Visual Studio mogą być podzielone na następujące kategorie menu:

##### <a name="core-menus"></a>Menu Core

-   Plik

-   Edytowanie

-   Widok

-   Narzędzia

-   Okno

-   Pomoc

##### <a name="project-specific-menus"></a>Menu specyficzne dla projektu

-   Projekt

-   Kompilacja

-   Debugowanie

##### <a name="context-specific-menus"></a>Menu kontekstowe

-   Zespół

-   Dane

-   Test

-   Architektura

-   Analiza

##### <a name="document-specific-menus"></a>Menu specyficzne dla dokumentu

-   Format

-   tabela

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Podczas projektowania menu głównych, należy stosować się do tych reguł:

-   Nie może przekraczać 25 elementów najwyższego poziomu w podanym kontekście

-   Menu nigdy nie powinna przekraczać 600 pikseli wysokości.

-   Ocenia menu głównego w wielu sytuacjach, takich jak w wersji Ultimate i profil ogólne.

-   Menu wysuwane są akceptowane.

-   Menu wysuwane powinien zawierać co najmniej trzy elementy i nie więcej niż siedem.

-   Menu wysuwane powinien przeprowadzić tylko jeden poziom głębokiego — niektóre elementy menu programu Visual Studio zawierają kaskadowych podmenu, ale tego wzorca nie zaleca się.

-   Użyj nie więcej niż sześciu separatorów. Grupowania należy stosować się do poniższej ilustracji:

     ![Wytyczne dotyczące grupowanie w menu głównym](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501 b_MainMenus")

-   Gdy masz każda grupa na rysunku nie jest wymagany, dodając dodatkowe grupowania jest ograniczona.

-   Każda grupa powinna mieć dwa na siedem elementów menu.

#### <a name="main-menu-ordering"></a>Kolejność menu głównego
 Przed dodaniem nowego elementu najwyższego poziomu, należy rozważyć umieszczenie polecenia do istniejącego menu najwyższego poziomu. Podczas dodawania nowego menu najwyższego poziomu, należy umieścić we właściwym miejscu. Zdecyduj, czy menu jest specyficzne dla projektu, kontekstu lub dokumentu. Zachowaj nazwę najwyższego poziomu menu zwięzły i użyj tylko jeden wyraz.

 Menu core powinna zakładkę pozostałe polecenia. Plik, Edytuj i Wyświetl powinien zawsze w lewo i okna narzędzi i pomocy powinna zawsze być po prawej stronie.

#### <a name="context-menus"></a>Menu kontekstowe
 Umieszczenie zbyt wiele funkcji w obrębie menu kontekstowe wyników w interfejsie zgodnym trudne do nauczenia się. Wszystkie najważniejsze funkcje powinny być dostępne za pośrednictwem paska menu głównego. Położenie poleceń należy uzgodnić przy użyciu istniejących poleceń, aby uniknąć zduplikowanych poleceń. Menu kontekstowe powłoki definiuje grupy standardowe menu, które mają zostać uwzględnione w zależności od tego, czy menu kontekstowe rozwiązania, węzeł projektu lub elementu projektu.

 Podczas projektowania menu kontekstowe należy stosować się do tych samych zasad, jak w przypadku menu głównego, a ponadto:

-   Nie może przekraczać 25 elementów menu górnego poziomu.

-   Menu wysuwane są akceptowane, ale musi nie może przekraczać jeden poziom głębokiego — nigdy nie używaj kaskadowych menu wysuwanych.

-   Użyj nie więcej niż sześciu separatorów.

### <a name="command-placement-in-toolbars"></a>Położenie polecenia na paskach narzędzi

#### <a name="general-toolbars"></a>Ogólne pasków narzędzi
 Podczas projektowania i rozmieszczanie paski narzędzi, postępuj zgodnie z tymi standardami:

-   Nie należy używać więcej niż jeden zlecenie na przycisku. Jeden przycisk = jedną akcję.

-   Użyj tekstu, obok ikony, tylko wtedy, gdy musi być wzmocnione z etykietą.

-   Użyj pola kombi wyłącznie dla właściwości, które zostaną przełączone wielokrotnie w jednej sesji. W przeciwnym razie można ujawnić właściwości w innym miejscu.

-   Szerokość pola kombi powinna być równa szerokości elementu najdłuższy w polu + 30%. Na przykład jeśli najdłuższy element znajduje się 200 pikseli, pole kombi należy 260 pikseli szerokości.

-   Ogranicz użycie separatorów. Użyj separatora obok listy rozwijanej jest wzorzec niezalecane, ponieważ kształt z listy rozwijanej, sama działa jako separatora wizualnego.

-   Ikona grupy powinna zawierać od 3 do 6 ikon.

-   Jeśli kwalifikatory spowodują pojawienie się wiele przydatnych poleceń, użyj przycisku podziału, która przechowuje ostatniego ustawienia:

     ![Podziel przycisków w programie Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501 c_SplitButtons")

     **Przykład przycisku podziału. Sześć poleceń po lewej stronie, zamiast tego można dopasować do jednego przycisku.**

#### <a name="product-specific-toolbars"></a>Paski narzędzi specyficznych dla produktu
 Każdego produktu może zapewnić, że domyślna pasek narzędzi, który zawiera często używane i ważne poleceń i narzędzi domyślnej każdego produktu powinna zostać wyświetlona przy pierwszym uruchomieniu programu Visual Studio po zainstalowaniu produktu.

 Produkty również należy korzystać z grup udostępnionych poleceń i menu, udostępniane przez środowisko IDE. Każda grupa udostępnionego polecenia jest umieszczany w udostępnionym menu przeznaczone do organizowania powiązanych poleceń w znaczący sposób dla użytkownika. Należy korzystać z tej struktury udostępnionego polecenia w celu zmniejszenia złożoności.

#### <a name="global-toolbars"></a>Globalne paski narzędzi
 Paski narzędzi globalne są wymagane do mieści się na jeden wiersz po prawej stronie gotowe. Podczas tworzenia nowych narzędzi globalnego, postępuj zgodnie z wytycznymi dla tego typu narzędzi.

 **Pasek narzędzi ogólne wytyczne:**

- Każdy narzędzi ma 24 pikseli formantów wspólnych (uchwytu, przepełnienie).

- Każdy przycisk paska narzędzi jest 22 pikseli szerokości, w tym dopełnienia. Tworzenie ikony przycisku podziału dodaje inny 11 pikseli szerokości.

- Duplikowanie poleceń na paskach narzędzi jest dozwolone.

  **Paski narzędzi specyficznych dla dokumentu** są wyświetlane, gdy określony typ pliku jest aktywny i znikają w przypadku uaktywniania innym typem pliku.

- Paski narzędzi specyficznych dla dokumentu nie może mieć więcej niż 12 przycisków.

- Łączna szerokość paska narzędzi nie może przekraczać 300 pikseli.

- Każdy typ pliku może mieć jeden osadzonym pasku narzędzi lub jeden globalny pasek narzędzi specyficznych dla dokumentu, ale nie oba.

  **Paski narzędzi specyficznych dla kontekstu** są wyświetlane, gdy pewnym kontekście jest ustawiona i zwykle pozostają aktywne przez dłuższy czas.

- Przycisk dla wszystkich pasków narzędzi specyficznych dla kontekstu wynoszący 18.

- Jeśli większość użytkowników nie będzie stale stosować poleceń tym paska narzędzi, gdy kontekst jest aktywny, następnie nie skojarzyć ten pasek narzędzi z kontekstem.

- Upewnij się, że pasek narzędzi zniknie podczas zamykania kontekstu. Żadna z nich powinna pojawić się podczas uruchamiania.

  **Paski narzędzi z kontekstu** nigdy nie pojawiają się automatycznie. Pokazują one, tylko gdy użytkownik aktywuje je. Zachowaj maksymalną szerokość poniżej 200 pikseli.

### <a name="general-organization-and-shell-defined-groups"></a>Ogólnej organizacji i grupy zdefiniowane powłoki
 Użyj istniejących udostępnionych poleceń, grup poleceń i menu. Jeśli nowego polecenia musi być zdefiniowana, spróbuj umieścić go w istniejącej grupie udostępnionego polecenia. Jeśli nowa grupa musi być zdefiniowana, spróbuj umieścić go w istniejącego menu udostępnionego blisko grupą powiązanych poleceń przed utworzeniem nowego menu najwyższego poziomu. Pozwala to zmniejszyć złożoność polecenia przy jednoczesnym zapewnieniu położenie polecenia spójne w środowisku IDE.

 Wspólnie **Format** menu, zwykle są wyświetlane w kontekście okien projektanta stylu dokumentu, przedstawiono na poniższej ilustracji:

 ![Visual Studio napisanego z objaśnieniami](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501 d_FormatMenu")

 **Grupy menu w programie Visual Studio**

### <a name="reducing-and-reusing-commands"></a>Zmniejszenie i ponowne użycie polecenia
 Polecenia są zwykle wyświetlane zależności w kontekście, w celu zmniejszenia liczby poleceń, który użytkownik zobaczy w danym momencie. Jednakże należy również używać ponownie istniejących udostępnionych menu i grup poleceń, aby upewnić się, że struktura polecenia pozostaje względnie czasu trwania stanu stabilnego między zmianami w kontekście.

 Ponowne użycie udostępnionych poleceń i wprowadzania nowych poleceń blisko powiązane polecenia udostępnionego zmniejsza złożoność środowiska IDE i tworzy użytkownikom większy komfort pracy.

## <a name="naming-commands"></a>Nadawanie nazw poleceń

### <a name="naming-conventions"></a>Konwencje nazewnictwa
 Polecenie spójnego nazewnictwa jest krytyczna, dzięki czemu użytkownicy mogą znaleźć i wykonywać polecenia, korzystając z wiersza polecenia lub powiązanie ze skrótem klawiaturowym. Nazwy poleceń również pomóc użytkownikowi zrozumieć, jakie przeznaczenia służy polecenie, gdy jest on wyświetlany na pasku narzędzi lub menu kaskadowych lub kontekstu.

#### <a name="when-naming-commands"></a>Podczas nazywania polecenia:

-   Skonstruuj tekst tak, aby łatwo możliwych do zlokalizowania. Więcej informacji na temat lokalizowanie tekstu, zobacz [gotowości World dla programu Visual Studio](http://msdn.microsoft.com/en-us/1cc35051-8126-441f-bea9-059245a47b1d).

-   Być zwięzłe. Polecenia należy używać co najwyżej trzech słów.

-   Stosowanie wielkimi literami liter: powinny być napisane wielkimi literami pierwszą literę każdego wyrazu. Aby uzyskać więcej informacji na temat formatowania tekstu w programie Visual Studio, zobacz [styl tekstu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

-   Wziąć pod uwagę, w którym zostaną umieszczone polecenia. Jest to w menu najwyższego poziomu lub menu wysuwanego? Na przykład podczas grupowania poleceń w menu wysuwane, a polecenia najwyższego poziomu musi być "Align" i poleceń menu wysuwane powinien być "Left" "Prawa", "Centrum", "Justify" i tak dalej. Zbyteczna nazwy poleceń menu wysuwane "Wyrównaj do lewej" lub "Wyrównaj do prawej".

     ![Visual Studio napisanego](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502 a_FormatMenu")

### <a name="using-icons-with-commands"></a>Za pomocą poleceń przy użyciu ikon
 Można spare użycie ikony parowania z poleceniami. Mimo że kojarzenie unikatowego obrazu za pomocą polecenia hastens zdolność użytkownika do identyfikowania tego polecenia, visual bałaganu i dotyczące nieefektywności wystąpić w przypadku nadużyciami obrazu. Następujące reguły pomoc przy podejmowaniu decyzji, czy ikona polecenia tworzenia.

#### <a name="use-an-icon-with-a-command-only-if"></a>Ikona za pomocą polecenia tylko wtedy, gdy:

-   To samo polecenie zawiera ikonę skojarzonych z nim w innym wyraźną produktu firmy Microsoft, takich jak jedna z aplikacji Microsoft Office.

-   Polecenie zostaną umieszczone w domyślnej paska narzędzi.

-   Polecenie jest polecenie specjalistyczne, które użytkownicy mogą dodać za pomocą narzędzi **"Dostosowywanie..."** okna dialogowego.

## <a name="access-and-shortcut-keys"></a>Klucze dostępu i skrótów

### <a name="overview"></a>Omówienie
 Istnieją dwa rodzaje klawiatury przypisań klawiszy:

-   **Klucze dostępu** (znany także jako akceleratorów) Zezwalaj na klawiatury uzyskać dostęp za pośrednictwem menu dla polecenia i każdej etykiety w oknie dialogowym interfejsu użytkownika. Klucze dostępu są głównie do celów ułatwień dostępu, są przypisywane do wszystkich menu i większość formantów okna dialogowego, nie mają być zapamiętanych, mają wpływ tylko bieżącego okna i są zlokalizowane.

-   **Klawisze skrótów** służy głównie kontrolki (Ctrl) oraz kombinacje klawiszy — funkcja (Fn). Są one przeznaczone bardziej dla użytkowników zaawansowanych i pomocy produktywności. One przypisanych tylko do większości często używanych poleceń i umożliwia szybki dostęp podczas z pominięciem menu głównego. Klawisze skrótów mają być zapamiętanych, a do tego powodu musi być przypisany spójne ze schematem profilu. Skrót klucza schematów mogą się różnić profilu profilu. Użytkownik może dostosować klawiszy skrótów, za pośrednictwem **Narzędzia > Opcje > klawiatury**.

### <a name="assigning-access-keys"></a>Przypisywanie klawiszy
 Klucze dostępu składają się z klawisze Alt plus alfanumeryczne. Przypisz klucza dostępu do każdego elementu menu, bez wyjątku. Postępuj zgodnie z Windows i typowych Konwencji przypisywanie klawiszy. na przykład klucz dostępu dla **Plik > Nowy** powinna zawsze być **Alt, F, N**.

 Nie używają liter pojedynczego pikseli szerokości, takie jak "i" (w wielkie lub małe) lub małą literą "l" i unikać używania znaków z wydłużeń (g, "j", p, pytania i y), jak te są trudne do odróżniania.

 Należy unikać używania zduplikowane klucze, gdy jest to możliwe. W przypadku dublowania nieuniknione menu system obsługuje konflikty cyklicznie przez wszystkie polecenia, które używają klucza. Na przykład możesz "Number" poleceń w menu Plik, która duplikuje klucza dostępu "N", aby uzyskać **Alt, F, N** utworzyć nowy plik i **Alt, F, N, N** wykona polecenia "Number".

### <a name="assigning-shortcut-keys"></a>Przypisywanie klawiszy skrótów
 Należy unikać przypisywania nowe klawisze skrótów, ponieważ nie są wymagane dla każdego polecenia i opodatkowaniem systemu (i pamięci użytkownika), jeśli nadmiernie obciążany. Dane z programu poprawy jakości obsługi klienta (CEIP) wskazuje, czy użytkownicy programu Visual Studio przy użyciu tylko mały podzbiór zintegrowane skróty.

 Podczas definiowania skróty, należy wykonać następujące czynności:

- **Za pomocą kontrolki (Ctrl) i sekwencji klawiszy — funkcja (Fn).**

- **Zachowaj często stosowane skróty.** Obsługa najpopularniejszych skróty.

- **Ułatw wpisz skróty dla edytora.** Skróty — w typie należy powiązać polecenia, że deweloperzy muszą większość podczas pisania kodu. Na przykład **Edit.InvokeSmartTag** musi mieć klucz skrót, takie jak Ctrl +/ i nie Alt + Shift + F10.

- **Dążenie do spójnego motywem skróty.**

- **Postępuj zgodnie z wytycznymi Windows, aby ustalić, które modyfikator kluczy mogą wykorzystać.** Użyj kombinacji klawiszy Ctrl dla polecenia, które mają wpływ na dużą skalę, takich jak polecenia, które są stosowane do całego dokumentu. Użyj kombinacji klawisza Shift dla poleceń, które rozszerzyć lub uzupełniają działania klawisza skrótu standard. Nie należy używać kombinacji klawiszy Ctrl + Alt.

- **Usuń skróty nadmiarowe.** Jeśli masz starszej wersji funkcji, rozważ usunięcie skróty, które są używane z infrequency extreme (mniej niż 10 razy w danych programu CEIP) lub umiarkowane infrequency (mniej niż 100 razy dane programu CEIP), jeśli klucz dostępu zapewnia szybki dostęp do tego samego polecenia. Na przykład: C ALT-H, spowoduje to otwarcie/spis treści pomocy.

  Nie jest to prosty sposób sprawdzić dostępność skrótów. Jeśli chcesz dodać skrót, wykonaj następujące kroki:

1.  Sprawdź listę [skróty programu Visual Studio 2013](http://visualstudioshortcuts.com/2013/) można sprawdzić, czy są podobne polecenia, aby Twoje z grupy.

2.  Przejdź do **Narzędzia > Opcje > środowisko > klawiatury** i przetestować skrót. Sprawdź, czy każdy schemat mapowania klawiatury na liście "Zastosuj poniższy schemat mapowania dodatkowej klawiatury". Profile ogólne, C#, VB i C++, należy sprawdzić, jak udostępniać te skróty unikatowy. Skrót jest dostępna, jeśli nie jest zamapowany we wszystkich tych miejscach.