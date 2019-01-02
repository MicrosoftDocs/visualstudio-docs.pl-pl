---
title: Podstawy interfejsu użytkownika dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6cd0824d245e835159e3887ce7286b2e55876ba3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53874876"
---
# <a name="ux-essentials-for-visual-studio"></a>Podstawy interfejsu użytkownika dla programu Visual Studio
## <a name="best-practices"></a>Najlepsze rozwiązania  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Zachowaj spójność w środowisku Visual Studio.  
  
-   Postępuj zgodnie z istniejącą [wzorce interakcji](interaction-patterns-for-visual-studio.md) powłoki.  
  
-   Projektowanie funkcji, aby były zgodne z językiem visual powłoki i [wymagania craftsmanship](evaluation-tools-for-visual-studio.md).  
  
-   Użyj udostępnionego poleceń i kontrolek, jeśli takie istnieją.  
  
-   Dowiedz się, w hierarchii programu Visual Studio i jak ustanawia kontekst i dyski interfejsu użytkownika.  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Usługa środowiska czcionek i kolorów.  
  
-   Interfejs użytkownika, należy przestrzegać bieżącego [czcionka środowiska](fonts-and-formatting-for-visual-studio.md) ustawienia, chyba że jest uwidaczniany dla dostosowania na stronie czcionek i kolorów w oknie dialogowym Opcje.  
  
-   Elementy interfejsu użytkownika, należy użyć [usługi VSColor](colors-and-styling-for-visual-studio.md), używana jest udostępniona tokeny środowiska lub tokenów specyficzne dla funkcji.  
  
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
 - Jest minimalna rozdzielczość dla programu Visual Studio Dev14 **1280 x 720**. Oznacza to, że jest *możliwe* używać programu Visual Studio w tym rozdzielczości, chociaż może nie być optymalne komfortu. Nie ma żadnej gwarancji, że wszystkie aspekty będzie użyteczny w rozdzielczości niższa niż 1280 x 720.  
  
 - Rozdzielczość docelowego dla programu Visual Studio jest **1366 x 768**. Jest to rozwiązanie najniższy, jaką Obiecujemy, *dobre* środowisko użytkownika.

 - Wysokość początkowego okna dialogowego powinna być **mniejszych niż 700 pikseli**, więc mieści się w minimalna rozdzielczość klatki IDE przy rozdzielczości 96 dpi.
  
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
  
 W tym przypadku jest kwestią dodatkowych, ponieważ zawiera Ikona używana dla alertu "&times;" ikony, więc nie można używać wspólnych ikonę Usuń obok niej. W rezultacie interfejsu użytkownika używa przycisk Usuń, bardziej clunky kontroli.  
  
 ![Wprowadzenie do interfejsu użytkownika w stanie błędu, domyślnie jest to wzorzec oprogramowanie Visual Studio. ](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti wzorzec")<br />Wprowadzenie do interfejsu użytkownika w stanie błędu, domyślnie jest to wzorzec oprogramowanie Visual Studio.
  
#### <a name="alternatives"></a>Alternatywy  
 Jest dużo lepszym rozwiązaniem tego problemu:  
  
-   Zezwalaj użytkownikowi na dodawanie deklaracji bez ostrzeżenia, a następnie przesuń od razu do ustawiania właściwości w elemencie.  
  
-   Dodaj ikonę ostrzeżenia (trójkąt gold) po fokusu z elementu, takie jak dodanie innej deklaracji do listy lub podejmują próby zmiany karty w projektancie.  
  
-   Jeśli użytkownik spróbuje kart przed ustawieniem właściwości na wszelkich deklaracji, pop, okno dialogowe wyjaśniające, że aplikacja nie zostanie skompilowany (lub dowolnego skutków) do momentu ostrzeżenia zostały rozwiązane. Jeśli użytkownik odrzuci okna dialogowego i zmienia karty mimo to następnie ikony (krytyczny lub ostrzegawczy, odpowiednio) jest dodawany do zakładki deklaracje.  
  
### <a name="multiple-clicks-to-dismiss-ui"></a>Kilka kliknięć, aby zamknąć interfejs użytkownika  
  
#### <a name="feature-team-goals"></a>Funkcja cele zespołu  
 Nie Zezwalaj użytkownikowi na zamknąć interfejs użytkownika bez pierwszy wyświetlany tekst wyjaśnienia.  
  
#### <a name="anti-pattern"></a>Zapobieganie wzorzec  
 Zespół Wstawianie wideo łącza do różnych miejscach interfejsu użytkownika programu VS zdecydowała się przed wspólny wzorzec "&times;" Zamknij objaśnienie przycisku i etykietek narzędzi, jak określone przez środowiska użytkownika i zamiast tego wykonuje listy rozwijanej, a link "Nie pokazuj ponownie".  

#### <a name="example-video-links-in-team-explorer"></a>Przykład: linki wideo w programie Team Explorer
Wymuszanie użytkownikowi odczyt tekst objaśnienia przed odrzucanie interfejsu użytkownika jest zapobieganie wzorzec, w programie Visual Studio. Prawidłowo zaprojektowana łącza wideo powinna zostać wyświetlona etykietka narzędzia z dodatkowymi informacjami na po wskazaniu wskaźnikiem, a następnie klikając polecenie "&times;" należy odrzucić wiadomości, bez konieczności dalszej interakcji.


 ![Tekst objaśniający ochrony przed złośliwym&#45;wzorzec &#45; niepoprawne](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />Wzorzec niepoprawny link do wideo
  
#### <a name="result"></a>Wynik  
 Zamiast przycisku Zamknij proste (jednym kliknięciem) użytkownik jest zmuszony wystarczy zamknąć interfejs użytkownika w każdym miejscu, które wideo łącza są wyświetlane przy użyciu dwóch kliknięć.  
  
#### <a name="alternatives"></a>Alternatywy  
 Poprawny projekt w tej sytuacji może być oparte na wzorcu common Internet Explorer, pakietu Office i programu Visual Studio: po najechaniu wskaźnikiem, użytkownik może wyświetlić opis etykietki narzędzia i jednym kliknięciem ukrywa interfejs użytkownika.  
  
 ![Tekst objaśniający ochrony przed złośliwym&#45;wzorzec &#45; poprawne](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Popraw wzorzec Explanatorytextanti")<br />Wzorzec prawidłowy link do wideo
  
### <a name="using-command-bars-for-settings"></a>Za pomocą pasków poleceń dla ustawień  
 **Rysunek** reprezentuje ten wzorzec niezalecane: umieszczanie ustawienie poniżej przycisku polecenia, który ma zastosowanie do więcej niż tylko polecenia. W tym szkic istnieją polecenia oprócz Rozpocznij debugowanie — Wyświetl w przeglądarce, Rozpocznij bez debugowania i Wkrocz, takich jak — która będzie uwzględniać wybrane ustawienie.  

  ![Rysunek Odp.: Wzorzec Układ paska poleceń](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "FigureA-Commandbaranti — wzorzec")<br />Rysunek Odp.: Wzorzec zapobieganie pasek poleceń
  
 Nieco lepiej, ale nadal niepożądanych, jest umieszczenie ustawienia tego typu w paski narzędzi, jak pokazano na **B rysunek**. Przyciski dzielone zajmują mniej miejsca i są w związku z tym poprawę za pośrednictwem list rozwijanych, oba projekty są nadal przy użyciu paska narzędzi do podwyższenia poziomu coś, co tak naprawdę nie jest poleceniem.  
 
 ![Rysunek B: Lepsze, ale nadal wzorzec przed pasku polecenia](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "FigureB-Commandbaranti — wzorzec")<br />Rysunek B: Lepsze, ale nadal wzorzec zapobieganie pasek poleceń
 
  W właściwe podejście pokazano w **rysunek C**, to ustawienie jest powiązany z serię poleceń. Nie ma żadnego ustawienia globalne, ustawiania i firma Microsoft jest po prostu przełączanie między czterech poleceń. Jest to tylko sytuacji, w którym polecenia na pasku narzędzi są akceptowane. 

 ![Rysunek C: Popraw Użyj wzorca paska poleceń programu Visual Studio](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "FigureC-Commandbaranti — wzorzec")<br />Rysunek C: Prawidłowe użycie wzorca paska poleceń programu Visual Studio
   
### <a name="control-anti-patterns"></a>Niezalecane wzorce kontrolki  
 Niektóre niezalecane wzorce są po prostu nieprawidłowe użycie lub prezentacji formantu lub grupy formantów.  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Podkreślenie używana jako etykieta grupy, nie hiperłącza  
 Podkreślenie tekst powinien być stosowany tylko dla hiperlinków.  
  
 **Zły:**    
 ![Podkreślony tekst, który nie jest hiperłącze to wzorzec oprogramowanie Visual Studio. ](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102 g_GroupLabelIncorrect")<br />Podkreślony tekst, który nie jest hiperłącze to wzorzec oprogramowanie Visual Studio.
  
 **Dobre:**   
 ![Różne poprawnie, bez hiperlink tekst jest wyświetlany unadorned czcionką środowiska. ](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102 h_GroupLabelCorrect")<br />Różne poprawnie, bez hiperlink tekst jest wyświetlany unadorned czcionką środowiska.
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Kliknij pole wyboru skutkuje wyskakującego okna dialogowego  
 Kliknięcie pola wyboru "Włącz pulpit zdalny dla wszystkich ról", w kreatorze "Publikowanie Windows Azure aplikacji" od razu powoduje wyświetlenie wyskakującego okna dialogowego wzorzec oprogramowanie Visual Studio. Ponadto, pole wyboru nie wypełniać pola wyboru po wybraniu, inny wzorca zapobieganie interakcji.  
  
 ![Dzięki temu okno dialogowe po kliknięcie pola wyboru jest to wzorzec oprogramowanie Visual Studio. ](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102 i_CheckboxPopup")<br />Dzięki temu okno dialogowe po kliknięcie pola wyboru jest to wzorzec oprogramowanie Visual Studio.
  
### <a name="hyperlink-anti-patterns"></a>Niezalecane wzorce dotyczące hiperłącza  
 Poniższy przykład zawiera dwa niezalecane wzorce.  
  
1. Pierwszego planu, włączając czerwony po najechaniu wskaźnikiem oznacza, że nie jest używany prawidłowy kolor udostępnionych usługi czcionki.  
  
2. "Dowiedz się więcej" nie jest odpowiedni tekst łącza do tematu pojęciowego. Celem użytkownika jest nie Aby dowiedzieć się więcej, aby zrozumieć zagadnienia wybranych przez nich.  
  
   ![Ignorowanie usługi kolorów i za pomocą "Dowiedz się więcej" dla hiperlinków są niezalecane wzorce dotyczące programu Visual Studio. ](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")<br />Ignorowanie usługi kolorów i za pomocą "Dowiedz się więcej" dla hiperlinków są niezalecane wzorce dotyczące programu Visual Studio.  
  
   **Lepszym rozwiązaniem:** Stanowić pytanie, na które użytkownik może zadać, klikając link.  
  
-   Jak działają usługi Windows Azure?  
  
-   Jeśli potrzebny jest projekt Windows Azure Mobile Services?  
  
#### <a name="using-click-here-for-links"></a>Za pomocą "Kliknij tutaj" dla łączy  
 Hiperlinki powinien być samoopisowe. Jest to niezalecane wzorzec używaj "sformułowania kliknij tutaj" lub dowolnych wariantów podobne.  
  
 **Zły:** "Kliknij tutaj, aby uzyskać instrukcje dotyczące sposobu tworzenia nowego projektu."
  
 **Dobre:** "Jak utworzyć nowy projekt?"