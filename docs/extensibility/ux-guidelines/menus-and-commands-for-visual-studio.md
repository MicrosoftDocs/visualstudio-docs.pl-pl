---
title: Menu i polecenia dla programu Visual Studio | Microsoft Docs
description: Dowiedz się, jak paski poleceń umożliwiają elastyczność w interfejsie użytkownika podczas tworzenia nowych funkcji dla programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1061de343ae24dce163dd0a7665d58ec7aac3a3a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068391"
---
# <a name="menus-and-commands-for-visual-studio"></a>Menu i polecenia dla programu Visual Studio
## <a name="command-usage"></a>Użycie polecenia

### <a name="overview"></a>Omówienie
 W przeciwieństwie do Microsoft Office, który jest zestawem obejmującym wiele oddzielnych produktów, program Visual Studio zawiera wiele produktów, które współtworzą zestawy poleceń w globalnym środowisku IDE programu Visual Studio. IDE zarządza złożonością tysięcy poleceń przez filtrowanie funkcji dostępnych dla użytkownika na podstawie kontekstu.

 Gdy zmiany kontekstu użytkownika — takie jak przełączanie z okna projektu do okna edycji kodu — funkcja niezwiązana z nowym kontekstem znika. W tym samym czasie nowe funkcje są dostępne razem z powiązanymi informacjami dynamicznymi, takimi jak właściwości i opcje przybornika. Użytkownik nie powinien zauważyć zamiany dostępnego zestawu poleceń. Jeśli użytkownik jest rozpraszany lub mylić z poleceniami, które pojawiają się lub znikają, projekt interfejsu użytkownika wymaga korekty. Bieżący kontekst użytkownika jest zawsze wskazywany na co najmniej jeden sposób, na przykład na pasku tytułu IDE, w okno Właściwości lub w oknie dialogowym strony właściwości.

 Paski poleceń umożliwiają elastyczność w interfejsie użytkownika. Jedyne struktury poleceń związane ze środowiskiem programu Visual Studio to menu główne i główny pasek poleceń, które można dostosować i nawet ukryć. Inne paski poleceń są wyświetlane i znikają w zależności od stanu aplikacji. Okna narzędzi i edytory dokumentów mogą również zawierać osadzone paski narzędzi w obrębie swoich krawędzi okna.

#### <a name="basic-guidelines"></a>Podstawowe wytyczne

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Jeśli to możliwe, Użyj istniejących poleceń udostępnionych, grup poleceń i menu.
 Ponieważ polecenia są zwykle wyświetlane na podstawie kontekstu, użycie istniejących menu udostępnianych i grup poleceń zapewnia, że struktura poleceń pozostaje stosunkowo stabilna między zmianami w kontekście. Ponowne używanie udostępnionych poleceń i umieszczanie nowych poleceń blisko powiązanych poleceń udostępnia również zmniejsza złożoność środowiska IDE i tworzy więcej przyjaznych dla użytkownika funkcji. Jeśli trzeba zdefiniować nowe polecenie, spróbuj je umieścić w istniejącej grupie poleceń udostępnionych. Jeśli trzeba zdefiniować nową grupę, należy ją umieścić w istniejącym menu udostępnionym blisko powiązanej grupy poleceń przed utworzeniem nowego menu najwyższego poziomu.

##### <a name="do-not-create-icons-for-every-command"></a>Nie należy tworzyć ikon dla każdego polecenia.
 Przed utworzeniem ikony polecenia należy uważnie myśleć. Ikony należy tworzyć tylko dla poleceń, które:

- pojawia się na domyślnym pasku narzędzi.

- mogą być dodawane przez użytkowników do paska narzędzi za pomocą okna dialogowego **Dostosowywanie...** .

- ikona skojarzona z tą samą akcją w innym produkcie firmy Microsoft.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Ograniczanie dodawania skrótów klawiaturowych
 Ogromna większość użytkowników korzysta z niewielkiej części wszystkich dostępnych skrótów. W razie wątpliwości nie należy powiązać funkcji ze skrótem klawiaturowym. Pracuj z zespołem środowiska użytkownika przed dodaniem nowych skrótów.

##### <a name="give-commands-a-default-menu-placement"></a>Nadaj poleceń domyślne położenie menu.
 Należy pamiętać, że polecenia będą dostosowywane przez inne osoby i odpowiednio projektować. Nie ma takich rzeczy jako polecenie ukryte. Wszystkie polecenia programu Visual Studio są wyświetlane w **narzędziu > Dostosowywanie** okna dialogowego, okno polecenia, Autouzupełnianie, **narzędzia > opcje > klawiatura** i środowisko narzędzi programistycznych (DTE). Upewnij się, że polecenia nazwa i etykietka narzędzia znajdują się w pliku. CTC, aby użytkownicy mogli je łatwo odnaleźć.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Nie należy duplikować poleceń udostępnionych na osadzonym pasku narzędzi.
 Warto umieścić polecenia w pobliżu obszaru fokusu użytkownika. W tym celu należy utworzyć osadzony pasek narzędzi u góry okna narzędzi lub edytora dokumentów. Polecenia umieszczone na pasku narzędzi powinny być specyficzne dla obszaru zawartości w oknie. Nie należy duplikować poleceń udostępnionych na tych paskach narzędzi. Na przykład nigdy nie należy umieszczać ikony "Save" w osadzonym pasku narzędzi.

### <a name="content-and-command-visibility"></a>Widoczność zawartości i poleceń
 Polecenia istnieją w następujących zakresach: **Environment**, **Hierarchy** i **Document**. Należy znać każdy zakres, aby mieć pewność, że w rozmieszczeniu poleceń.

 Polecenia w zakresie **środowiska** określają kontekst podstawowy i są współużytkowane przez wiele kontekstów. Zmieniają widoczność lub rozmieszczenie dokumentów i okien narzędzi. Między poleceniami w zakresie środowiska są **nowe projekty**, **Połącz z serwerem**, **Dołączaj proces**, **Wytnij**, **Kopiuj**, **Wklej**, **Znajdź**, **Opcje**, **Dostosuj**, **nowe okno** i **Wyświetlaj pomoc**.

 Polecenia w zakresie **hierarchii** zarządzają hierarchiami w programie Visual Studio, w tym **projektami**, **zespołem** i **danymi**. Są one powiązane z podkontekstem projektu — na przykład **debugowanie**, **Kompilowanie**, **testowanie**, **Architektura** lub **Analizowanie**. Między poleceniami w zakresie hierarchii są **dodawane nowe elementy**, **nowe zapytania**, **Ustawienia projektu**, **Dodaj nowe źródło danych**, **Uruchom Kreatora wydajności** i **Nowy diagram**.

 Polecenia w zakresie **dokumentu** działają dla zawartości dokumentu, takiego jak kod, projekt lub kwerenda elementu pracy (wiq). Działają one również w widoku okna narzędzi lub są specyficzne dla tego okna narzędzia. Polecenia zakresu dokumentu działają również na obiektach plików, które są same dla hierarchii, na przykład **Usuń z projektu**. Między poleceniami w zakresie dokumentu są **refaktoryzacje > Zmień nazwę**, **Utwórz kopię elementu pracy**, **Rozwiń wszystko**, **Zwiń wszystko** i **Utwórz zadanie użytkownika**.

### <a name="command-placement-decisions"></a>Decyzje dotyczące umieszczania poleceń
 Po podjęciu decyzji o utworzeniu polecenia należy określić jego odpowiednie położenie i zdecydować, czy ma zostać utworzony skrót klawiaturowy. Postępuj zgodnie z tą ścieżką decyzji, aby określić, gdzie umieścić polecenie:

 ![Wykres decyzyjny umieszczania polecenia](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501 — a_CommandPlacement")

 **Ścieżka decyzji dotycząca umieszczenia poleceń w programie Visual Studio**

### <a name="command-placement-in-menus"></a>Umieszczenie polecenia w menu

#### <a name="main-menu-bar"></a>Główny pasek menu
 Główny pasek menu powinien być lokalizacją standardową dla poleceń wszystkich pakietów menu specyficznych dla kontekstu, które przyczyniają się do interfejsu użytkownika. Główny pasek menu różni się od innych struktur poleceń, które są używane przez środowisko do kontrolowania, które polecenia są widoczne. Wszystkie inne paski poleceń po prostu wyłączą polecenia, które są poza kontekstem, niezależnie od tego, czy są umieszczone w menu, czy na pasku narzędzi.

 Środowisko definiuje zestaw poleceń wbudowanych w głównym pasku menu, które są wspólne w całym środowisku IDE i wielu domenach zadań. Te polecenia są zawsze widoczne niezależnie od tego, które pakietów VSPackage są ładowane do środowiska. Mimo że pakietów VSPackage może rozciągnąć ten zestaw poleceń, należy ustawić polecenie z każdego produktu i rozmieszczenie ich poleceń jako odpowiedzialności poszczególnych zespołów.

 Strukturę menu głównego programu Visual Studio można podzielić na następujące kategorie menu:

##### <a name="core-menus"></a>Podstawowe menu

- Plik

- Edytuj

- Widok

- narzędzia

- Okno

- Help

##### <a name="project-specific-menus"></a>Menu specyficzne dla projektu

- Project

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

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Podczas projektowania głównych menu przestrzegaj następujących reguł:

- Nie przekraczaj 25 elementów najwyższego poziomu w danym kontekście

- Menu nie powinno nigdy przekraczać 600 pikseli.

- Oceń menu główne w wielu kontekstach, na przykład w końcowej wersji SKU i w profilu ogólnym.

- Menu wysuwane są akceptowalne.

- Menu wysuwane powinny zawierać co najmniej trzy elementy i nie więcej niż siedem.

- Menu wysuwane powinny zawierać tylko jeden poziom głębokie — niektóre elementy menu programu Visual Studio mają kaskadowe podmenu, ale nie jest to zalecane.

- Użyj nie więcej niż sześciu separatorów. Grupowania powinny być zgodne z poniższą ilustracją:

     ![Wskazówki dotyczące grupowania menu głównego](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501 — b_MainMenus")

- Chociaż nie jest wymagane, aby każde grupowanie na rysunku było możliwe, dodawanie dodatkowych grupowań jest ograniczone.

- Każde grupowanie powinno zawierać od dwóch do siedmiu elementów menu.

#### <a name="main-menu-ordering"></a>Porządkowanie menu głównego
 Przed dodaniem nowego elementu najwyższego poziomu Rozważ umieszczenie polecenia w istniejącym menu najwyższego poziomu. Dodając nowe menu najwyższego poziomu, pamiętaj, aby umieścić je we właściwym miejscu. Zdecyduj, czy menu jest specyficzne dla projektu, kontekstu lub dokumentu. Należy zachować zwięzłą nazwę menu najwyższego poziomu i używać tylko jednego wyrazu.

 Podstawowe menu powinny Bookend resztę poleceń. Pliki, Edycja i widok powinny zawsze znajdować się po lewej stronie, a narzędzia, okna i pomoc powinny zawsze znajdować się w prawej części strony.

#### <a name="context-menus"></a>Menu kontekstowe
 Umieszczenie zbyt dużej funkcjonalności w menu kontekstowym skutkuje trudnym do uczeniem interfejsem. Wszystkie najważniejsze funkcje powinny być dostępne za pomocą głównego paska menu. Umieszczanie poleceń powinno być uzgadniane z istniejącymi poleceniami, aby uniknąć duplikowania poleceń. W przypadku menu kontekstowego powłoka definiuje standardowe grupy menu, które powinny być uwzględnione w zależności od tego, czy menu kontekstowe dotyczy rozwiązania, węzła projektu czy elementu projektu.

 Podczas projektowania menu kontekstowych stosuj się do tych samych zasad, co w menu głównym, a ponadto:

- Nie przekraczaj 25 elementów menu najwyższego poziomu.

- Menu wysuwane są akceptowalne, ale nie mogą być dłuższe niż jeden poziom głęboki — nigdy nie używaj kaskadowych menu podręcznych.

- Użyj nie więcej niż sześciu separatorów.

### <a name="command-placement-in-toolbars"></a>Umieszczanie poleceń w paskach narzędzi

#### <a name="general-toolbars"></a>Ogólne paski narzędzi
 Podczas projektowania i rozmieszczania pasków narzędzi postępuj zgodnie z następującymi standardami:

- Nie używaj więcej niż jednego zlecenia na przycisk. Jeden przycisk = jedna akcja.

- Używaj tekstu obok ikony tylko wtedy, gdy trzeba ją wzmocnić przy użyciu etykiety.

- Użyj pola kombi wyłącznie dla właściwości, które zostaną przełączone wiele razy w jednej sesji. W przeciwnym razie Uwidocznij właściwość w innym miejscu.

- Szerokość pola kombi powinna być równa szerokości najdłuższego elementu w polu + 30%. Na przykład jeśli najdłuższy element ma 200 pikseli, pole kombi powinno zawierać 260 pikseli szerokości.

- Ogranicz użycie separatorów. Użycie separatora obok listy rozwijanej jest antywzorca, ponieważ kształt listy rozwijanej działa jako separator wizualny.

- Grupy ikon powinny zawierać od trzech do sześciu ikon.

- Jeśli kwalifikatory powodują wiele przydatnych poleceń, użyj przycisku podziału, który przechowuje ostatnie ustawienie:

     ![Przyciski podziału w programie Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501 — c_SplitButtons")

     **Przykład przycisku podziału. Sześć poleceń po lewej stronie może w zamian dopasować się do jednego przycisku.**

#### <a name="product-specific-toolbars"></a>Paski narzędzi specyficzne dla produktu
 Każdy produkt może udostępnić domyślny pasek narzędzi, który zawiera często używane i ważne polecenia, a każdy z domyślnych pasków narzędzi każdego produktu powinien pojawić się po pierwszym uruchomieniu programu Visual Studio po zainstalowaniu produktu.

 Produkty powinny również korzystać z udostępnionych grup poleceń i menu dostarczonych przez środowisko IDE. Każda udostępniona Grupa poleceń jest umieszczana w menu udostępnionym przeznaczonym do organizowania powiązanych poleceń w zrozumiały sposób dla użytkownika. Ważne jest, aby wykorzystać tę udostępnioną strukturę poleceń, aby zmniejszyć złożoność.

#### <a name="global-toolbars"></a>Globalne paski narzędzi
 Globalne paski narzędzi są wymagane do dopasowania do jednego wiersza po prawej stronie pola. Podczas tworzenia nowego globalnego paska narzędzi postępuj zgodnie z wytycznymi dla tego typu paska narzędzi.

 **Ogólne wytyczne dotyczące pasków narzędzi:**

- Każdy pasek narzędzi ma 24 piksele w wspólnych kontrolkach (uchwyt, przepełnienie).

- Każdy przycisk paska narzędzi ma wysokość 22 pikseli, włącznie z uzupełnieniem. Ikona przycisku podziału dodaje kolejne 11 pikseli szerokości.

- Duplikowanie poleceń w paskach narzędzi jest dozwolone.

  **Paski narzędzi specyficzne dla dokumentu** pojawiają się, gdy określony typ pliku jest aktywny i znika, gdy zostanie uaktywniony inny typ pliku.

- Paski narzędzi specyficznych dla dokumentu nie mogą mieć więcej niż 12 przycisków.

- Łączna szerokość paska narzędzi nie może przekraczać 300 pikseli.

- Każdy typ pliku może mieć jeden osadzony pasek narzędzi lub jeden globalny pasek narzędzi specyficzny dla dokumentu, ale nie oba.

  **Paski narzędzi specyficznych dla kontekstu** są wyświetlane, gdy określony kontekst jest ustawiony i ma być aktywny przez dłuższy okres.

- Limit przycisków dla wszystkich pasków narzędzi specyficznych dla kontekstu to 18.

- Jeśli większość użytkowników nie będzie regularnie korzystać z poleceń tego paska narzędzi, gdy kontekst jest aktywny, nie kojarz tego paska narzędzi z kontekstem.

- Upewnij się, że pasek narzędzi znika podczas kończenia kontekstu. Żaden z tych pasków narzędzi nie powinien znajdować się podczas uruchamiania.

  **Paski narzędzi bez kontekstu** nigdy nie pojawiają się automatycznie. Są one wyświetlane tylko wtedy, gdy użytkownik je aktywuje. Zachowaj maksymalną szerokość poniżej 200 pikseli.

### <a name="general-organization-and-shell-defined-groups"></a>Ogólna organizacja i grupy zdefiniowane w powłoce
 Użyj istniejących poleceń udostępnionych, grup poleceń i menu. Jeśli trzeba zdefiniować nowe polecenie, spróbuj je umieścić w istniejącej grupie poleceń udostępnionych. Jeśli trzeba zdefiniować nową grupę, spróbuj ją umieścić w istniejącym menu udostępnionym blisko powiązanej grupy poleceń przed utworzeniem nowego menu najwyższego poziomu. Zmniejsza to złożoność polecenia przy zapewnieniu spójnego umieszczania poleceń w środowisku IDE.

 Menu **Format** udostępniony, zwykle wyświetlane w kontekście okien dokumentu w stylu projektanta, przedstawiono na poniższej ilustracji:

 ![Menu formatu programu Visual Studio z objaśnieniami](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501 — d_FormatMenu")

 **Grupy menu w programie Visual Studio**

### <a name="reducing-and-reusing-commands"></a>Zmniejszanie i używanie poleceń
 Polecenia są zwykle wyświetlane na podstawie kontekstu, aby zmniejszyć liczbę poleceń widocznych dla użytkownika w danym momencie. Jednak należy również ponownie użyć istniejących udostępnionych menu i grup poleceń, aby upewnić się, że struktura poleceń pozostaje stosunkowo stabilna między zmianami w kontekście.

 Ponowne użycie udostępnionych poleceń i umieszczenie nowych poleceń blisko powiązanych poleceń udostępnionych zmniejsza złożoność środowiska IDE i tworzy więcej przyjaznych dla użytkownika funkcji.

## <a name="naming-commands"></a>Nazywanie poleceń

### <a name="naming-conventions"></a>Konwencje nazewnictwa
 Spójne nazewnictwo poleceń ma krytyczne znaczenie, aby użytkownicy mogli znajdować i wykonywać polecenia, przy użyciu wiersza polecenia lub powiązania ze skrótem klawiaturowym. Nazwy poleceń również pomagają użytkownikowi zrozumieć, jaki ma być polecenie, gdy jest ono wyświetlane na pasku narzędzi lub w menu kaskadowym lub.

#### <a name="when-naming-commands"></a>Podczas nazewnictwa poleceń:

- Utwórz tekst, aby można go było łatwo odróżniać. Aby uzyskać więcej informacji na temat lokalizowania tekstu, zobacz [najlepsze rozwiązania dotyczące lokalizacji](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices).

- Być zwięzłe. Polecenia powinny używać nie więcej niż trzech wyrazów.

- Użyj wielką literą wielkości liter: pierwsza litera każdego wyrazu powinna być pisany wielkimi literami. Aby uzyskać więcej informacji na temat formatowania tekstu w programie Visual Studio, zobacz [styl tekstu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

- Weź pod uwagę, gdzie zostanie umieszczone polecenie. Czy znajduje się on w menu najwyższego poziomu, czy w oknie wysuwanym? Na przykład podczas grupowania poleceń wyrównania w menu wysuwanym polecenie najwyższego poziomu powinno mieć wartość "Wyrównaj", a polecenia wysuwane powinny mieć wartość "Left", "" do prawej "," Center "," Wyjustuj "i tak dalej. Byłoby nadmiarowe, aby nazwać polecenia wysuwania "Wyrównaj do lewej" lub "Wyrównaj do prawej".

     ![Menu formatu programu Visual Studio](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502 — a_FormatMenu")

### <a name="using-icons-with-commands"></a>Używanie ikon z poleceniami
 Należy zastanowić się nad użyciem parowania ikon z poleceniami. Chociaż skojarzenie unikatowego obrazu z poleceniem hastens użytkownikowi możliwość zidentyfikowania tego polecenia, niewidocznych elementów wizualnych i niewydajnego wystąpienia obrazu. Poniższe reguły pomagają w wyborze, czy należy utworzyć ikonę polecenia.

#### <a name="use-an-icon-with-a-command-only-if"></a>Użyj ikony z poleceniem tylko wtedy, gdy:

- To samo polecenie ma skojarzoną z nim ikonę w innym, widocznym produkcie firmy Microsoft, na przykład w jednej z Microsoft Office aplikacji.

- Polecenie zostanie umieszczone na domyślnym pasku narzędzi.

- Polecenie to specjalistyczne polecenie, które użytkownicy mogą dodawać do paska narzędzi przy użyciu okna dialogowego **"Dostosowywanie..."** .

## <a name="access-and-shortcut-keys"></a>Klawisze dostępu i skrótów

### <a name="overview"></a>Omówienie
 Istnieją dwa rodzaje przypisań klawiszy klawiatury:

- **Klucze dostępu** (znane również jako akceleratory) zezwalają na dostęp za pomocą klawiatury za pośrednictwem menu poleceń i do każdej etykiety w interfejsie użytkownika okna dialogowego. Klucze dostępu są głównie na potrzeby ułatwień dostępu, są przypisywane do wszystkich menu i większości formantów okna dialogowego, nie są przeznaczone do Memorized, wpływają tylko na bieżące okno i są zlokalizowane.

- Skróty **klawiaturowe najczęściej** wykorzystują sekwencję klawiszy Control (Ctrl) i Function (Fn). Są one bardziej zaprojektowane dla zaawansowanych użytkowników i pomocy w produktywności. Są one przypisywane tylko do najczęściej używanych poleceń i umożliwiają szybki dostęp, jednocześnie pomijając menu główne. Skróty klawiaturowe mają być Memorized i z tego powodu muszą być przypisane do schematu profilu. Schematy klawiszy skrótów mogą się różnić od profilu do profilowania. Użytkownik może dostosować klawisze skrótów za pomocą **narzędzi > opcje > klawiaturą**.

### <a name="assigning-access-keys"></a>Przypisywanie kluczy dostępu
 Klucze dostępu składają się z klawiszy Alt i alfanumerycznych. Przypisz klucz dostępu do każdego elementu menu bez wyjątku. Należy przestrzegać systemu Windows i wspólnych Konwencji do przypisywania kluczy dostępu. na przykład klucz dostępu dla **pliku > New** powinien być zawsze **Alt, F, N**.

 Nie używaj liter o pojedynczej szerokości, takich jak "i" (wielkimi literami lub małymi literami), a także małych liter "l" i Unikaj używania znaków z dolnymi literami (g, j, p, q i y), ponieważ trudno jest odróżnić.

 Należy unikać używania zduplikowanych kluczy, jeśli jest to możliwe. W przypadkach, w których nie można uniknąć duplikowania, system menu obsługuje konflikty przez przechodzenie przez wszystkie polecenia, które używają klucza. Przykładowo dla hipotetycznego polecenia "number" w menu plik, które duplikuje klucz dostępu "N", **Alt, f, N** utworzy nowy plik, a **Alt, f, n, n** wykona polecenie "number".

### <a name="assigning-shortcut-keys"></a>Przypisywanie klawiszy skrótów
 Należy unikać przypisywania nowych klawiszy skrótów, ponieważ nie są one wymagane dla każdego polecenia i podatkiem systemowym (i pamięcią użytkownika), jeśli są używane. Dane z Program poprawy jakości obsługi klienta (CEIP) wskazują, że użytkownicy programu Visual Studio używają tylko małego podzestawu zintegrowanych skrótów.

 Podczas definiowania skrótów należy przestrzegać następujących reguł:

- **Użyj sekwencji klawiszy Control (Ctrl) i Function (Fn).**

- **Zachowaj często używane skróty.** Zachowaj najpopularniejsze skróty.

- **Ułatwiaj wpisywanie skrótów edytora.** Powiąż łatwe w wpisywanie skróty do poleceń, które deweloperzy potrzebują najczęściej podczas pisania kodu. Na przykład **Edycja. InvokeSmartTag** musi mieć szybki klawisz skrótu, taki jak Ctrl +/, a nie Alt + Shift + F10.

- **Dążą do spójnych skrótów.**

- **Postępuj zgodnie z wytycznymi systemu Windows, aby określić, które klucze modyfikatorów zastosować.** Użyj kombinacji klawiszy Ctrl dla poleceń, które mają efekty na dużą skalę, takich jak polecenia, które są stosowane do całego dokumentu. Użyj kombinacji klawiszy Shift dla poleceń, które zwiększają lub uzupełniają akcje standardowego klawisza skrótu. Nie używaj kombinacji klawiszy Ctrl + Alt.

- **Usuń obce skróty.** Jeśli masz starszą funkcję, Rozważ usunięcie skrótów, które są używane z ekstremalną częstotliwością (mniej niż 10 razy z danych programu CEIP) lub średnią nieczęstotliwością (mniej niż 100 razy z danych CEIP), jeśli klucz dostępu zapewnia szybki dostęp do tego samego polecenia. Na przykład: Alt, H, C otworzy pomoc/treść.

  Nie istnieje prosty sposób na sprawdzenie dostępności skrótów. Jeśli chcesz dodać skrót, wykonaj następujące kroki:

1. Zapoznaj się z listą [skrótów Visual Studio 2013](http://visualstudioshortcuts.com/2013/) , aby określić, czy są podobne polecenia do grupowania.

2. Przejdź do pozycji **narzędzia > opcje > środowisko > klawiatury** i Przetestuj swój skrót. Sprawdź każdy schemat mapowania klawiatury wymieniony w obszarze "Zastosuj następujący schemat mapowania dodatkowych klawiatur". Sprawdź profile ogólne, C#, VB i C++, ponieważ te unikatowe skróty są udostępniane. Skrót jest dostępny, jeśli nie jest zamapowany w żadnym z tych miejsc.
