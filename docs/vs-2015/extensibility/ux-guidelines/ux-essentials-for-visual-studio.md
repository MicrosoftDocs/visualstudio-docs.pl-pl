---
title: Podstawowe informacje dotyczące środowiska użytkownika
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5f207a6bd8ba4947617e6cc1212f92dcfe81516e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53940647"
---
# <a name="ux-essentials-for-visual-studio"></a>Podstawy interfejsu użytkownika dla programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="best-practices"></a>Najlepsze rozwiązania

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Zachowaj spójność w środowisku Visual Studio.

-   Postępuj zgodnie z istniejących wzorce interakcji powłoki.

-   Projektowanie funkcji, aby były zgodne z powłoki języka i craftsmanship wymagania visual.

-   Użyj udostępnionego poleceń i kontrolek, jeśli takie istnieją.

-   Dowiedz się, w hierarchii programu Visual Studio i jak ustanawia kontekst i dyski interfejsu użytkownika.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Usługa środowiska czcionek i kolorów.

-   Interfejs użytkownika należy przestrzegać bieżące ustawienia czcionek środowiska, o ile nie jest widoczna dla dostosowania na stronie czcionek i kolorów w oknie dialogowym Opcje.

-   Elementy interfejsu użytkownika, należy użyć usługi VSColor przy użyciu tokenów w środowisku współdzielonym lub tokenów specyficzne dla funkcji.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Wszystkie aplikacje należy zgodnie z nowym stylem programu VS.

-   Postępuj zgodnie z zasadami projektowania programu Visual Studio dla ikony, symbole i innych grafik.

-   Nie należy umieszczać tekstu w elementy graficzne.

### <a name="4-design-from-a-user-centric-perspective"></a>4. Projekt z punktu widzenia skoncentrowane na użytkowniku.

-   Utwórz przepływ zadań przed poszczególnych funkcji w nim.

-   Należy zapoznać się z użytkownikami, a następnie udostępnią tę wiedzę jawne w swojej specyfikacji.

-   Podczas przeglądania interfejsu użytkownika, należy obliczyć pełnego środowiska pracy, a także szczegółowe informacje.

-   Interfejs użytkownika projektuje się tak, aby pozostaje funkcjonalny i atrakcyjne niezależnie od ustawień regionalnych i językowych.

## <a name="screen-resolution"></a>Rozdzielczość ekranu

### <a name="minimum-resolution"></a>Minimalna rozdzielczość
 Minimalna rozdzielczość Dev14 usługi Visual Studio jest 1280 x 1024. Oznacza to, że jest *możliwe* używać programu Visual Studio w tym rozdzielczości, chociaż może nie być optymalne komfortu. Nie ma żadnej gwarancji, że wszystkie aspekty będzie użyteczny w rozdzielczości niższa niż 1280 x 1024.

 Rozmiar początkowy okna dialogowego nie powinna przekraczać 1000 pikseli wysokości, tak aby mieści się w ramce IDE, w tym minimalna rozdzielczość przy rozdzielczości 96 dpi.

### <a name="high-density-displays"></a>Wyświetla o wysokiej gęstości
 Interfejs użytkownika w programie Visual Studio musi działać poprawnie na wszystkich urządzeniach skalowania DPI, obsługiwanych przez Windows gotowych: 150%, 200% i 250%.

## <a name="anti-patterns"></a>Niezalecane wzorce dotyczące
 Program Visual Studio zawiera wiele przykładów interfejsu użytkownika, które należy wykonać nasze wskazówki i najlepsze rozwiązania. W ramach działań zmierzających do deweloperów często zapożyczonych z wzorce projektowania interfejsu użytkownika produktu podobnie jak co to jest tworzone. Mimo że jest to dobra metoda, że pomaga nam dysku spójności w interakcji z użytkownikiem i projektowania wizualnego, czasami publikujemy funkcji, korzystając z kilku szczegółowe informacje, które nie spełniają nasze wskazówki ze względu na ograniczenia harmonogramu lub wady priorytetyzacji. W takich przypadkach nie chcemy zespoły skopiowanie jednego z tych "niezalecane wzorce dotyczące", ponieważ mogą mnożyć się nieprawidłowe lub niekonsekwentnie interfejsu użytkownika w środowisku Visual Studio.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Wymagane pola/ustawienia domyślnie wyświetlany w stanie Błąd

#### <a name="feature-team-goals"></a>Funkcja cele zespołu

-   Należy ostrzec użytkowników, że dodali element, który musi być skonfigurowany.

-   Rysuj uwagi użytkownika do obszarów, które wymagają wprowadzania.

#### <a name="anti-pattern-solution"></a>Zapobieganie wzorzec rozwiązania
 Zaraz po użytkownik zainicjował akcję, a przed zakończenia zadania, natychmiast umieścić zatrzymanie krytyczne ikony obok obszarów, które wymagają konfiguracji.

#### <a name="example-manifest-designer-declarations"></a>Przykład: Deklaracje projektanta manifestu
 Dodawanie deklaracji do listy natychmiast umieszcza je w stanie błędu, który będzie się powtarzać, dopóki użytkownik ustawia wymaganych właściwości.

 W tym przypadku jest kwestią dodatkowych, ponieważ Ikona używana dla alertu zawiera symbol "x", aby usunąć typowe ikony nie można używać obok niej. W rezultacie interfejsu użytkownika używa przycisk Usuń, bardziej clunky kontroli.

 ![Manifest Designer deklaracji błąd ochrony przed złośliwym&#45;wzorzec](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti wzorzec")

 **Wprowadzenie do interfejsu użytkownika w stanie błędu, domyślnie jest to wzorzec oprogramowanie Visual Studio.**

#### <a name="alternatives"></a>Alternatywy
 Jest dużo lepszym rozwiązaniem tego problemu:

-   Zezwalaj użytkownikowi na dodawanie deklaracji bez ostrzeżenia, a następnie przesuń od razu do ustawiania właściwości w elemencie.

-   Dodaj ikonę ostrzeżenia (trójkąt gold) po fokusu z elementu, takie jak dodanie innej deklaracji do listy lub podejmują próby zmiany karty w projektancie.

-   Jeśli użytkownik spróbuje kart przed ustawieniem właściwości na wszelkich deklaracji, pop, okno dialogowe wyjaśniające, że aplikacja nie zostanie skompilowany (lub dowolnego skutków) do momentu ostrzeżenia zostały rozwiązane. Jeśli użytkownik odrzuci okna dialogowego i zmienia karty mimo to następnie ikony (krytyczny lub ostrzegawczy, odpowiednio) jest dodawany do zakładki deklaracje.

### <a name="forcing-the-user-to-read-text-before-dismissing-ui"></a>Wymuszanie użytkownikowi odczyt tekstu przed odrzucanie interfejsu użytkownika

#### <a name="feature-team-goals"></a>Funkcja cele zespołu
 Nie Zezwalaj użytkownikowi na zamknąć interfejs użytkownika bez pierwszy wyświetlany tekst wyjaśnienia.

#### <a name="anti-pattern"></a>Zapobieganie wzorzec
 Zespołu Wstawianie wideo łącza do różnych miejscach interfejsu użytkownika programu VS, przeciwko wspólny wzorzec X Zamknij przycisku i etykietek narzędzi wyjaśnienie określony przez UX i zamiast tego zaimplementowane listy rozwijanej, a link "Nie pokazuj ponownie".

 ![Tekst objaśniający ochrony przed złośliwym&#45;wzorzec &#45; niepoprawne](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")

 **Niepoprawne: Wymuszenie użytkownikowi odczyt tekst objaśnienia przed odrzucanie interfejsu użytkownika jest zapobieganie wzorzec, w programie Visual Studio.**

#### <a name="result"></a>Wynik
 Zamiast przycisku Zamknij proste (jednym kliknięciem) użytkownik jest zmuszony wystarczy zamknąć interfejs użytkownika w każdym miejscu, które wideo łącza są wyświetlane przy użyciu dwóch kliknięć.

#### <a name="alternatives"></a>Alternatywy
 Poprawny projekt w tej sytuacji może być oparte na wzorcu common Internet Explorer, pakietu Office i programu Visual Studio: po najechaniu wskaźnikiem, użytkownik może wyświetlić opis etykietki narzędzia i jednym kliknięciem ukrywa interfejs użytkownika.

 ![Tekst objaśniający ochrony przed złośliwym&#45;wzorzec &#45; poprawne](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Popraw wzorzec Explanatorytextanti")

 **Prawidłowe: zgodnie z założeniami linki wideo powinna zostać wyświetlona etykietka narzędzia z dodatkowymi informacjami po najechaniu wskaźnikiem i klikając przycisk "X" należy odrzucić wiadomości, bez konieczności dalszej interakcji.**

### <a name="using-command-bars-for-settings"></a>Za pomocą pasków poleceń dla ustawień
 ![Pasek poleceń ochrony przed złośliwym&#45;wzorzec &#45; rysunek](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "FigureA-Commandbaranti — wzorzec")

 **Rysunek Odp.: Wzorzec zapobieganie pasek poleceń**

 **Rysunek** reprezentuje ten wzorzec niezalecane: umieszczanie ustawienie poniżej przycisku polecenia, który ma zastosowanie do więcej niż tylko polecenia. W tym szkic istnieją polecenia oprócz Rozpocznij debugowanie — Wyświetl w przeglądarce, Rozpocznij bez debugowania i Wkrocz, takich jak — która będzie uwzględniać wybrane ustawienie.

 ![Pasek poleceń ochrony przed złośliwym&#45;wzorzec &#45; B rysunek](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "FigureB-Commandbaranti — wzorzec")

 **Rysunek B: Lepsze, ale nadal wzorzec zapobieganie pasek poleceń**

 Nieco lepiej, ale nadal niepożądanych, jest umieszczenie ustawienia tego typu w paski narzędzi, jak pokazano na **B rysunek**. Przyciski dzielone zajmują mniej miejsca i są w związku z tym poprawę za pośrednictwem list rozwijanych, oba projekty są nadal przy użyciu paska narzędzi do podwyższenia poziomu coś, co tak naprawdę nie jest poleceniem.

 ![Pasek poleceń ochrony przed złośliwym&#45;wzorzec &#45; C rysunek](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "FigureC-Commandbaranti — wzorzec")

 **Rysunek C: Prawidłowe użycie wzorca paska poleceń programu Visual Studio**

 W **rysunek C**, to ustawienie jest powiązany z serię poleceń. Nie ma żadnego ustawienia globalne, ustawiania i firma Microsoft jest po prostu przełączanie między czterech poleceń. Jest to tylko sytuacji, w którym polecenia na pasku narzędzi są akceptowane.

### <a name="control-anti-patterns"></a>Niezalecane wzorce kontrolki
 Niektóre niezalecane wzorce są po prostu nieprawidłowe użycie lub prezentacji formantu lub grupy formantów.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Podkreślenie używana jako etykieta grupy, nie hiperłącza
 Podkreślenie tekst powinien być stosowany tylko dla hiperlinków.

 **Zły:**

 ![Podkreślenie ochrony przed złośliwym&#45;wzorca w etykiecie grupy](../../extensibility/ux-guidelines/media/0102-g-grouplabelincorrect.png "0102 g_GroupLabelIncorrect")

 **Podkreślony tekst, który nie jest hiperłącze to wzorzec oprogramowanie Visual Studio.**

 **Dobre:**

 ![Podkreślenie ochrony przed złośliwym&#45;wzorca w etykiecie grupy &#40;poprawne&#41;](../../extensibility/ux-guidelines/media/0102-h-grouplabelcorrect.png "0102 h_GroupLabelCorrect")

 **Różne poprawnie, bez hiperlink tekst jest wyświetlany unadorned czcionką środowiska.**

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Kliknij pole wyboru skutkuje wyskakującego okna dialogowego
 Kliknięcie pola wyboru "Włącz pulpit zdalny dla wszystkich ról", w kreatorze "Publikowanie Windows Azure aplikacji" od razu powoduje wyświetlenie wyskakującego okna dialogowego wzorzec oprogramowanie Visual Studio. Ponadto, pole wyboru nie wypełniać pola wyboru po wybraniu, inny wzorca zapobieganie interakcji.

 ![Zaznacz pole wyboru pop&#45;chroniących się&#45;wzorzec](../../extensibility/ux-guidelines/media/0102-i-checkboxpopup.png "0102 i_CheckboxPopup")

 **Dzięki temu okno dialogowe po kliknięcie pola wyboru jest to wzorzec oprogramowanie Visual Studio.**

### <a name="hyperlink-anti-patterns"></a>Niezalecane wzorce dotyczące hiperłącza
 Poniższy przykład zawiera dwa niezalecane wzorce.

1. Pierwszego planu, włączając czerwony po najechaniu wskaźnikiem oznacza, że nie jest używany prawidłowy kolor udostępnionych usługi czcionki.

2. "Dowiedz się więcej" nie jest odpowiedni tekst łącza do tematu pojęciowego. Celem użytkownika jest nie Aby dowiedzieć się więcej, aby zrozumieć zagadnienia wybranych przez nich.

   ![Hiperłącze ochrony przed złośliwym&#45;wzorców](../../extensibility/ux-guidelines/media/0102-j-hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")

   **Ignorowanie usługi kolorów i za pomocą "Dowiedz się więcej" dla hiperlinków są niezalecane wzorce dotyczące programu Visual Studio.**

   **Lepszym rozwiązaniem:** Stanowić pytanie, na które użytkownik może zadać, klikając link.

-   Jak działają usługi Windows Azure?

-   Jeśli potrzebny jest projekt Windows Azure Mobile Services?

#### <a name="using-click-here-for-links"></a>Za pomocą "Kliknij tutaj" dla łączy
 Hiperlinki powinien być samoopisowe. Jest to niezalecane wzorzec używaj "sformułowania kliknij tutaj" lub dowolnych wariantów podobne.

 **Zły:** "Kliknij tutaj, aby uzyskać instrukcje dotyczące sposobu tworzenia nowego projektu."

 **Dobre:** "Jak utworzyć nowy projekt?"
