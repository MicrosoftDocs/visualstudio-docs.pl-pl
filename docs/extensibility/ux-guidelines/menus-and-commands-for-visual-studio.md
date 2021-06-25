---
title: Menu i polecenia dla Visual Studio | Microsoft Docs
description: Dowiedz się, jak paski poleceń zapewniają elastyczność interfejsu użytkownika podczas tworzenia nowych funkcji dla Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ef66123e1a4d62f89fc1c69b81bcb780d0b294f0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902101"
---
# <a name="menus-and-commands-for-visual-studio"></a>Menu i polecenia dla programu Visual Studio
## <a name="command-usage"></a>Użycie poleceń

### <a name="overview"></a>Omówienie
 W Microsoft Office, który jest pakietem składającym się z wielu oddzielnych produktów, Visual Studio zawiera wiele produktów, z których każdy współtwoczy zestawy poleceń w globalnym Visual Studio IDE. Ide zarządza złożonością tysięcy poleceń przez filtrowanie funkcji dostępnych dla użytkownika na podstawie kontekstu.

 Gdy kontekst użytkownika zmienia się — na przykład przełączanie z okna projektowania na okno edycji kodu — znika funkcjonalność niepowiązana z nowym kontekstem. Jednocześnie nowe funkcje są wraz z powiązanymi informacjami dynamicznymi, takimi jak właściwości i opcje przybornika. Użytkownik nie powinien zauważyć zamiany dostępnego zestawu poleceń. Jeśli użytkownik jest rozpraszany lub mylący przez pojawiające się lub znikające polecenia, projekt interfejsu użytkownika wymaga korekty. Bieżący kontekst użytkownika jest zawsze wskazywany na jeden lub więcej sposobów, na przykład na pasku tytułu środowiska IDE, okno Właściwości lub w oknie dialogowym Strony właściwości.

 Paski poleceń zapewniają elastyczność w interfejsie użytkownika. Jedyne struktury poleceń związane ze środowiskiem Visual Studio to menu główne i główny pasek poleceń, które można dostosowywać, a nawet ukrywać. Inne paski poleceń są wyświetlane i znika w zależności od stanu aplikacji. Okna narzędzi i edytory dokumentów mogą również zawierać osadzone paski narzędzi w krawędziach okna.

#### <a name="basic-guidelines"></a>Podstawowe wskazówki

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Używaj istniejących udostępnionych poleceń, grup poleceń i menu zawsze, gdy jest to możliwe.
 Ponieważ polecenia są zwykle wyświetlane na podstawie kontekstu, użycie istniejących udostępnionych menu i grup poleceń zapewnia, że struktura poleceń pozostaje względnie stabilna między zmianami w kontekście. Ponowne ponowne używać udostępnionych poleceń i umieszczanie nowych poleceń w pobliżu powiązanych poleceń udostępnionych zmniejsza również złożoność środowiska IDE i tworzy środowisko bardziej przyjazne dla użytkownika. Jeśli trzeba zdefiniować nowe polecenie, spróbuj umieścić je w istniejącej udostępnionej grupie poleceń. Jeśli trzeba zdefiniować nową grupę, umieść ją w istniejącym menu udostępnionym w pobliżu powiązanej grupy poleceń przed utworzeniem nowego menu najwyższego poziomu.

##### <a name="do-not-create-icons-for-every-command"></a>Nie twórz ikon dla każdego polecenia.
 Zastanów się przed utworzeniem ikony polecenia. Ikony należy tworzyć tylko dla poleceń, które:

- na domyślnym pasku narzędzi.

- prawdopodobnie zostaną dodane przez użytkowników do paska narzędzi za pośrednictwem okna **dialogowego Dostosowywanie....**

- mieć ikonę skojarzoną z tą samą akcją w innym produkcie firmy Microsoft.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Ogranicz dodawanie skrótów klawiaturowych
 Ogromna większość użytkowników stosuje niewielką część wszystkich dostępnych skrótów. W razie wątpliwości nie powiąż funkcji ze skrótem klawiaturowym. Przed dodaniem nowych skrótów należy współpracować z zespołem obsługi użytkowników.

##### <a name="give-commands-a-default-menu-placement"></a>Nadaj poleceniam domyślne umieszczanie menu.
 Należy pamiętać, że polecenia zostaną dostosowane przez inne osoby i odpowiednio je zaprojektują. Nie ma czegoś takiego jak ukryte polecenie. Wszystkie Visual Studio są wyświetlane w oknie dialogowym Narzędzia **> Dostosowywanie,** oknie polecenia, automatycznym ukończeniu, oknie dialogowym Tools > Options > Keyboard (Narzędzia **> Klawiatura)** i środowisku narzędzi programistyznych (DTE). Pamiętaj, aby nadać poleceniam nazwę i etykietkę narzędzia w pliku ctc, aby użytkownicy mogą je łatwo znaleźć.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Nie duplikuj udostępnionych poleceń na osadzonym pasku narzędzi.
 Warto umieszczać polecenia w pobliżu obszaru fokusu użytkownika. Jednym ze sposobów na to jest utworzenie osadzonego paska narzędzi w górnej części okna narzędzi lub edytora dokumentów. Polecenia umieszczone na pasku narzędzi powinny być specyficzne dla regionu zawartości w oknie. Nie duplikuj udostępnionych poleceń na tych paskach narzędzi. Na przykład nigdy nie umieszczaj ikony "Zapisz" na osadzonym pasku narzędzi.

### <a name="content-and-command-visibility"></a>Widoczność zawartości i poleceń
 Polecenia istnieją w następujących zakresach: **środowisko,** **hierarchia** i **dokument**. Poznaj każdy zakres, aby mieć pewność co do rozmieszczenia poleceń.

 Polecenia w zakresie **środowiska** ustanawiają kontekst podstawowy i są współużytkują je między wieloma kontekstami. Zmieniają one widoczność lub rozmieszczenie dokumentów i okien narzędzi. Do poleceń w zakresie środowiska **należą: Nowy** **projekt,** Łączenie z **serwerem,** Dołączanie **procesu,** **Wycinanie,** **Kopiowanie,** Wklejanie, **Znajdowanie,** **Opcje,** **Dostosowywanie,** **Nowe okno** i **Wyświetlanie pomocy.**

 Polecenia w zakresie **hierarchii** zarządzają hierarchiami w Visual Studio, w tym **Project,** **Team** i **Data.** Odnoszą się one do podkontekstu projektu — na przykład **debugować,** kompilować, **testować,** **architekturę** lub **analizować**. Do poleceń w zakresie hierarchii należą: **Add New Item**(Dodaj nowy element), New Query (Nowe **zapytanie),** **Project Settings**(Ustawienia projektu), Add New **Data Source**(Dodawanie nowego źródła danych), Launch Performance Wizard **(Kreator wydajności** uruchamiania) i New Diagram **(Nowy diagram).**

 Polecenia w **zakresie** dokumentu działają na zawartość dokumentu, taką jak kod, projekt lub zapytanie elementu roboczego (WIQ). Działają one również w widoku okna narzędzi lub w inny sposób są specyficzne dla tego okna narzędzi. Polecenia zakresu dokumentu działają również na obiektach plików, które same w sobie są specyficzne dla hierarchii, takich jak **Usuń z projektu**. Do poleceń w zakresie dokumentu należą Refaktoryzacja, > **Zmień** **nazwę,** Utwórz kopię elementu roboczego, Rozwiń wszystko, **Zwiń** wszystko i Utwórz zadanie **użytkownika.**

### <a name="command-placement-decisions"></a>Decyzje dotyczące umieszczania poleceń
 Po utworzeniu polecenia należy określić jego odpowiednie położenie i określić, czy należy utworzyć skrót klawiaturowy. Postępuj zgodnie z tą ścieżką podejmowania decyzji, aby ustalić, gdzie umieścić polecenie:

 ![Wykres decyzji o umieszczeniu poleceń](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-a_CommandPlacement")

 **Ścieżka decyzji dotyczącej umieszczania poleceń w Visual Studio**

### <a name="command-placement-in-menus"></a>Umieszczanie poleceń w menu

#### <a name="main-menu-bar"></a>Pasek menu głównego
 Pasek menu głównego powinien być standardową lokalizacją poleceń wszelkich pakietów menu kontekstowych, które współtworyzowały interfejs użytkownika. Pasek menu głównego różni się od innych struktur poleceń tym, że środowisko używa go do kontrolowania, które polecenia są widoczne. Wszystkie inne paski poleceń po prostu wyłączają polecenia, które są poza kontekstem, niezależnie od tego, czy są one umieszczane w menu, czy na pasku narzędzi.

 Środowisko definiuje zestaw poleceń wbudowanych na pasku menu głównego, które są wspólne dla całego środowiska IDE i wielu domen zadań. Te polecenia są zawsze widoczne niezależnie od tego, które pakiet VSPackages są ładowane do środowiska. Mimo że pakiet VSPackages może rozszerzyć ten zestaw poleceń, za zestaw poleceń z każdego produktu i umieszczanie ich poleceń odpowiada każdy zespół.

 Strukturę menu Visual Studio można podzielić na następujące kategorie menu:

##### <a name="core-menus"></a>Menu podstawowe

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

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Podczas projektowania menu głównych należy przestrzegać następujących reguł:

- Nie należy przekraczać 25 elementów najwyższego poziomu w danym kontekście

- Menu nigdy nie powinno przekraczać 600 pikseli wysokości.

- Oceń menu główne w wielu kontekstach, takich jak Ultimate SKU i Profil ogólny.

- Menu wysuwu jest dopuszczalne.

- Menu wysuwu powinno zawierać co najmniej trzy elementy i nie więcej niż siedem elementów.

- Menu wysuwu powinno mieć tylko jeden poziom głębokości — niektóre Visual Studio menu mają kaskadowe podmenu, ale ten wzorzec nie jest zachęcany.

- Nie używaj więcej niż sześciu separatorów. Grupowania powinny być zgodne z następującą ilustracją:

     ![Wskazówki dotyczące grupowania menu głównego](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501-b_MainMenus")

- Chociaż nie jest wymagane, aby każde grupowanie było na rysunku, dodawanie dodatkowych grupowania jest ograniczone.

- Każde grupowanie powinno mieć od dwóch do siedmiu elementów menu.

#### <a name="main-menu-ordering"></a>Kolejność menu głównego
 Przed dodaniem nowego elementu najwyższego poziomu rozważ umieszczenie polecenia w istniejącym menu najwyższego poziomu. Podczas dodawania nowego menu najwyższego poziomu należy umieścić je we właściwej lokalizacji. Zdecyduj, czy menu jest specyficzne dla projektu, kontekstu, czy dokumentu. Zachowaj zwięzłą nazwę menu najwyższego poziomu i używaj tylko jednego wyrazu.

 Menu podstawowe powinny zostać zarezerwowane dla pozostałych poleceń. Ustawienia Plik, Edycja i Widok powinny zawsze być po lewej stronie, a narzędzia, okno i pomoc powinny zawsze być po prawej stronie.

#### <a name="context-menus"></a>Menu kontekstowe
 Umieszczenie zbyt dużej funkcjonalności w menu kontekstowym powoduje trudne do nauczenia się interfejsu. Wszystkie główne funkcje powinny być dostępne za pośrednictwem paska menu głównego. Rozmieszczenie poleceń należy uzgodnić z istniejącymi poleceniami, aby uniknąć duplikowania poleceń. W przypadku menu kontekstowych powłoka definiuje standardowe grupy menu, które powinny zostać uwzględnione w zależności od tego, czy menu kontekstowe jest dla rozwiązania, węzła projektu, czy elementu projektu.

 Podczas projektowania menu kontekstowych należy stosować się do tych samych reguł, co w przypadku menu głównego, a ponadto:

- Nie należy przekraczać 25 elementów menu najwyższego poziomu.

- Menu wysuwu jest dopuszczalne, ale nie może przekraczać jednego poziomu głębokości — nigdy nie używaj kaskadowych wysuwów.

- Nie używaj więcej niż sześciu separatorów.

### <a name="command-placement-in-toolbars"></a>Umieszczanie poleceń na paskach narzędzi

#### <a name="general-toolbars"></a>Ogólne paski narzędzi
 Podczas projektowania i rozmieszczania pasków narzędzi postępuj zgodnie z tymi standardami:

- Nie używaj więcej niż jednego zlecenia na przycisk. Jeden przycisk = jedna akcja.

- Używaj tekstu obok ikony tylko wtedy, gdy trzeba go przechować za pomocą etykiety.

- Używaj pola kombi wyłącznie dla właściwości, które będą przełączane wiele razy w jednej sesji. W przeciwnym razie uwidocznij właściwość w innym miejscu.

- Szerokość pola kombi powinna być równa szerokości najdłuższego elementu w polu + 30%. Jeśli na przykład najdłuższy element ma 200 pikseli, pole kombi powinno mieć 260 pikseli szerokości.

- Ogranicz użycie separatorów. Użycie separatora obok listy rozwijanej jest antyw wzorzec, ponieważ kształt samej listy rozwijanej działa jako separator wizualny.

- Grupy ikon powinny zawierać od trzech do sześciu ikon.

- Jeśli kwalifikatory są wynikiem wielu przydatnych poleceń, użyj przycisku podziału, który przechowuje ostatnie ustawienie:

     ![Dzielenie przycisków w Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501-c_SplitButtons")

     **Przykład przycisku podziału. Sześć poleceń po lewej stronie można zamiast tego zmieścić w jednym przycisku.**

#### <a name="product-specific-toolbars"></a>Paski narzędzi specyficzne dla produktu
 Każdy produkt może zapewniać domyślny pasek narzędzi zawierający często używane i ważne polecenia, a domyślny pasek narzędzi każdego produktu powinien być wyświetlany przy pierwszym Visual Studio po zainstalowaniu produktu.

 Produkty powinny również korzystać z udostępnionych grup poleceń i menu udostępnianych przez ideę . Każda udostępniona grupa poleceń jest umieszczana w udostępnionym menu przeznaczonym do organizowania powiązanych poleceń w zrozumiały sposób dla użytkownika. Ważne jest, aby wykorzystać tę udostępnioną strukturę poleceń w celu zmniejszenia złożoności.

#### <a name="global-toolbars"></a>Globalne paski narzędzi
 Globalne paski narzędzi są wymagane, aby mieściły się w jednym wierszu od razu po opakowaniu. Podczas tworzenia nowego globalnego paska narzędzi postępuj zgodnie z wytycznymi dotyczącymi tego typu paska narzędzi.

 **Ogólne wskazówki dotyczące paska narzędzi:**

- Każdy pasek narzędzi ma 24 piksele wspólnych kontrolek (uchwyt, przepełnienie).

- Każdy przycisk paska narzędzi ma szerokość 22 pikseli, w tym wypełnienie. Dodanie ikony jako przycisku podziału powoduje dodanie kolejnych 11 pikseli szerokości.

- Duplikowanie poleceń na paskach narzędzi jest dozwolone.

  **Paski narzędzi specyficzne dla dokumentu są** wyświetlane, gdy określony typ pliku jest aktywny i zniknie, gdy inny typ pliku stanie się aktywny.

- Paski narzędzi specyficzne dla dokumentów mogą mieć nie więcej niż 12 przycisków.

- Całkowita szerokość paska narzędzi nie może przekraczać 300 pikseli.

- Każdy typ pliku może mieć jeden osadzony pasek narzędzi lub jeden globalny pasek narzędzi specyficzny dla dokumentu, ale nie oba.

  **Paski narzędzi kontekstowe są wyświetlane,** gdy określony kontekst jest ustawiony i zwykle pozostają aktywne przez dłuższy czas.

- Limit przycisków dla wszystkich kontekstowych pasków narzędzi wynosi 18.

- Jeśli większość użytkowników nie będzie spójnie stosować poleceń tego paska narzędzi, gdy kontekst jest aktywny, nie należy kojarzyć tego paska narzędzi z kontekstem.

- Upewnij się, że pasek narzędzi zniknie podczas zamykania kontekstu. Żaden z tych pasków narzędzi nie powinien być wyświetlany podczas uruchamiania.

  **Paski narzędzi bez kontekstu nigdy** nie są wyświetlane automatycznie. Są one wyświetlane tylko wtedy, gdy użytkownik aktywuje je. Zachowaj maksymalną szerokość poniżej 200 pikseli.

### <a name="general-organization-and-shell-defined-groups"></a>Ogólna organizacja i grupy zdefiniowane przez powłokę
 Użyj istniejących udostępnionych poleceń, grup poleceń i menu. Jeśli trzeba zdefiniować nowe polecenie, spróbuj umieścić je w istniejącej udostępnionej grupie poleceń. Jeśli trzeba zdefiniować nową grupę, spróbuj umieścić ją w istniejącym menu udostępnionym w pobliżu powiązanej grupy poleceń przed utworzeniem nowego menu najwyższego poziomu. Zmniejsza to złożoność poleceń przy jednoczesnym zapewnieniu spójnego umieszczania poleceń w idee IDE.

 Udostępnione menu **Format,** zwykle wyświetlane w kontekście okien dokumentów w stylu projektanta, jest przedstawione na poniższej ilustracji:

 ![Visual Studio Format z objaśnieniami](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501-d_FormatMenu")

 **Grupy menu w Visual Studio**

### <a name="reducing-and-reusing-commands"></a>Zmniejszanie i ponowne używać poleceń
 Polecenia są zwykle wyświetlane na podstawie kontekstu, aby zmniejszyć liczbę poleceń widocznych dla użytkownika w danym momencie. Należy jednak również ponownie używać istniejących udostępnionych menu i grup poleceń, aby upewnić się, że struktura poleceń pozostaje względnie stabilna między zmianami w kontekście.

 Ponowne używać udostępnionych poleceń i umieszczanie nowych poleceń w pobliżu powiązanych poleceń udostępnionych zmniejsza złożoność środowiska IDE i tworzy środowisko bardziej przyjazne dla użytkownika.

## <a name="naming-commands"></a>Polecenia nazewnictwa

### <a name="naming-conventions"></a>Konwencje nazewnictwa
 Spójne nazewnictwo poleceń ma kluczowe znaczenie, dzięki czemu użytkownicy mogą znaleźć i wykonywać polecenia przy użyciu wiersza polecenia lub powiązania ze skrótem klawiaturowym. Nazwy poleceń pomagają również użytkownikowi zrozumieć, jaki cel ma polecenie, gdy jest wyświetlane na pasku narzędzi lub w menu kaskadowym lub kontekstowym.

#### <a name="when-naming-commands"></a>Podczas nazewnictwa poleceń:

- Skonstruuj tekst, aby można go było łatwo zlokalizowane. Aby uzyskać więcej informacji na temat lokalizacji tekstu, zobacz [Najlepsze rozwiązania dotyczące lokalizacji](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices).

- Zwięzłe. Polecenia powinny używać nie więcej niż trzech wyrazów.

- Używaj liter tytuł-liter: pierwsza litera każdego wyrazu powinna być wyliczana na literę. Aby uzyskać więcej informacji na temat formatowania tekstu w Visual Studio, zobacz [Styl tekstu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

- Weź pod uwagę miejsce, w którym zostanie umieszczone polecenie. Czy znajduje się on w menu najwyższego poziomu, czy wysuwane? Na przykład podczas grupowania poleceń wyrównania w wysuwanych okienkach polecenie najwyższego poziomu powinno mieć grupę "Wyrównaj", a polecenia wysuwu powinny mieć wartości "Do lewej", "Do prawej", "Wyśrodkowanie", "Uzasadnienie" i tak dalej. Byłoby ono nadmiarowe, aby nazwać polecenia wysuwu "Wyrównaj do lewej" lub "Wyrównaj do prawej".

     ![Visual Studio format](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502-a_FormatMenu")

### <a name="using-icons-with-commands"></a>Używanie ikon z poleceniami
 Należy rozrzedzić użycie parowania ikon z poleceniami. Mimo że skojarzenie unikatowego obrazu z poleceniem umożliwia użytkownikowi zidentyfikowanie tego polecenia, nieład wizualny i nieefektywność występują w przypadku przemętowania obrazu. Poniższe reguły ułatwiają podjęcie decyzji o utworzeniu ikony polecenia.

#### <a name="use-an-icon-with-a-command-only-if"></a>Użyj ikony z poleceniem tylko wtedy, gdy:

- To samo polecenie ma ikonę skojarzoną z nim w innym znanym produkcie firmy Microsoft, takim jak jedna z Microsoft Office aplikacji.

- Polecenie zostanie umieszczone na domyślnym pasku narzędzi.

- Polecenie to specjalne polecenie, które użytkownicy mogą dodać do paska narzędzi przy użyciu **okna dialogowego "Dostosuj...".**

## <a name="access-and-shortcut-keys"></a>Klucze dostępu i skróty

### <a name="overview"></a>Omówienie
 Istnieją dwa rodzaje przypisań klawiszy klawiatury:

- **Klucze dostępu** (nazywane również akceleratorami) umożliwiają dostęp za pomocą klawiatury za pośrednictwem menu do poleceń i do każdej etykiety w interfejsie użytkownika okna dialogowego. Klucze dostępu są głównie przeznaczone dla ułatwień dostępu, są przypisywane do wszystkich menu i większości kontrolek okien dialogowych, nie są przeznaczone do zapamiętywania, mają wpływ tylko na bieżące okno i są zlokalizowane.

- **Klawisze skrótów** najczęściej używają sekwencji klawiszy Control (Ctrl) i Function (Fn). Są one zaprojektowane bardziej z myślą o zaawansowanych użytkownikach i wspomagają produktywność. Są one przypisywane tylko do najczęściej używanych poleceń i umożliwiają szybki dostęp przy pomijaniu menu głównego. Klawisze skrótów są przeznaczone do zapamiętywania i z tego powodu muszą być przypisane zgodnie ze schematem profilu. Schematy klawiszy skrótów mogą się różnić w zależności od profilu. Użytkownik może dostosować klawisze skrótów za **pomocą narzędzia > opcje > klawiatury**.

### <a name="assigning-access-keys"></a>Przypisywanie kluczy dostępu
 Klucze dostępu składają się z klawiszy Alt i alfanumerycznych. Przypisz klucz dostępu do każdego elementu menu bez wyjątku. Postępuj zgodnie z windows i typowe konwencje dotyczące przypisywania kluczy dostępu. Na przykład klucz dostępu dla nazwy **File > New** powinien zawsze mieć format **Alt, F, N**.

 Nie używaj liter o pojedynczej szerokości pikseli, takich jak "i" (wielkie lub małe litery) ani małych liter "l", i unikaj używania znaków z malejąco (g, j, p, q i y), ponieważ są one trudne do rozróżnienia.

 Unikaj używania zduplikowanych kluczy, jeśli jest to możliwe. W przypadkach, gdy duplikowanie jest nieuniknione, system menu obsługuje konflikty przez przechylenie za pośrednictwem wszystkich poleceń, które używają klucza. Na przykład w przypadku hipotetycznego polecenia "Liczba" w menu Plik, które duplikuje klucz dostępu "N", **Alt, F, N** utworzy nowy plik, a **Alt, F, N, N** wykona polecenie "Number".

### <a name="assigning-shortcut-keys"></a>Przypisywanie klawiszy skrótów
 Należy unikać przypisywania nowych klawiszy skrótów, ponieważ nie są one wymagane dla każdego polecenia i podają system (i pamięć użytkownika), jeśli są one nadwyręzone. Dane z Program poprawy jakości obsługi klienta (CEIP) wskazują, Visual Studio użytkownicy używają tylko niewielkiego podzestawu zintegrowanych skrótów.

 Podczas definiowania skrótów postępuj zgodnie z tymi regułami:

- **Użyj sekwencji klawiszy Control (Ctrl) i Function (Fn).**

- **Zachowaj często używane skróty.** Zachowaj najpopularniejsze skróty.

- **Ułatwiaj wpisywanie skrótów w edytorze.** Powiąż skróty łatwe do typu z poleceniami, których deweloperzy potrzebują najbardziej podczas pisania kodu. Na przykład element **Edit.InvokeSmartTag** musi mieć szybki klawisz skrótu, taki jak Ctrl+/, a nie Alt+Shift+F10.

- **Staraj się, aby skróty o spójnych tematach.**

- **Postępuj zgodnie z wytycznymi dla systemu Windows, aby określić, które klucze modyfikujące mają być stosowane.** Użyj kombinacji klawiszy Ctrl dla poleceń, które mają efekty na dużą skalę, takich jak polecenia, które mają zastosowanie do całego dokumentu. Użyj kombinacji klawiszy Shift dla poleceń, które rozszerzają lub uzupełniają akcje standardowego klawisza skrótu. Nie używaj kombinacji Ctrl+Alt.

- **Usuń nadmiarowe skróty.** Jeśli masz starszą funkcję, rozważ usunięcie skrótów używanych z bardzo rzadkimi okresami (mniej niż 10 razy w przypadku danych programu CEIP) lub umiarkowanym rzadko (mniej niż 100 razy z danych programu CEIP), jeśli klucz dostępu zapewnia szybki dostęp do tego samego polecenia. Na przykład: Alt, H, C spowoduje otwarcie okna Pomoc/zawartość.

  Nie ma prostego sposobu sprawdzania dostępności skrótów. Jeśli chcesz dodać skrót, wykonaj następujące kroki:

1. Sprawdź listę [skrótów Visual Studio 2013,](http://visualstudioshortcuts.com/2013/) aby ustalić, czy istnieją podobne polecenia do grupowania.

2. Przejdź do **opcji narzędzia > i > environment > i** przetestuj skrót. Sprawdź każdy schemat mapowania klawiatury wymieniony w obszarze "Zastosuj następujący dodatkowy schemat mapowania klawiatury". Zaznacz profile Ogólne, C#, VB i C++, ponieważ te profile współdzielą unikatowe skróty. Skrót jest dostępny, jeśli nie jest mapowany w żadnym z tych miejsc.
