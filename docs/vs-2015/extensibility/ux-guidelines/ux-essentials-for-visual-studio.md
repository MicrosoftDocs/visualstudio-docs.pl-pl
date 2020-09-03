---
title: Podstawowe informacje dotyczące środowiska użytkownika
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f3ed2d3f8bc52b21f6a87ac7d6da00f665f6b28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181365"
---
# <a name="ux-essentials-for-visual-studio"></a>Podstawy środowiska użytkownika dla programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="best-practices"></a>Najlepsze rozwiązania

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. być spójne w środowisku programu Visual Studio.

- Obserwuj istniejące wzorce interakcji w powłoce.

- Projektuj funkcje, które mają być zgodne z językiem wizualnym powłoki i wymaganiami craftsmanship.

- Użyj udostępnionych poleceń i kontrolek, gdy istnieją.

- Zapoznaj się z hierarchią programu Visual Studio i sposobem ustalania kontekstu i dysków interfejsu użytkownika.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Użyj usługi środowiska dla czcionek i kolorów.

- Interfejs użytkownika powinien uwzględniać bieżące ustawienie czcionki środowiska, chyba że zostanie uwidocznione na potrzeby dostosowywania na stronie czcionki i kolory w oknie dialogowym Opcje.

- Elementy interfejsu użytkownika muszą używać usługi VSColor przy użyciu tokenów środowiska udostępnionego lub tokenów specyficznych dla funkcji.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. wszystkie obrazy są spójne z nowym stylem programu VS.

- Postępuj zgodnie z zasadami projektowania programu Visual Studio dla ikon, symboli i innych grafik.

- Nie umieszczaj tekstu w elementach graficznych.

### <a name="4-design-from-a-user-centric-perspective"></a>4. Projektowanie z perspektywy zorientowanej na użytkownika.

- Utwórz przepływ zadań przed indywidualnymi funkcjami.

- Zapoznaj się z użytkownikami i zapoznaj się z tą wiedzą w Twojej specyfikacji.

- Podczas przeglądania interfejsu użytkownika należy oszacować pełne środowisko oraz szczegóły.

- Zaprojektuj interfejs użytkownika tak, aby pozostawał funkcjonalny i atrakcyjny niezależnie od ustawień regionalnych lub języka.

## <a name="screen-resolution"></a>Rozdzielczość ekranu

### <a name="minimum-resolution"></a>Minimalna rozdzielczość
 Minimalna rozdzielczość programu Visual Studio Dev14 to 1280x1024. Oznacza to, *że można korzystać z programu* Visual Studio w tym rozwiązaniu, chociaż może to nie być optymalne środowisko użytkownika. Nie ma gwarancji, że wszystkie aspekty będą użyteczne w rozdzielczościach mniejszych niż 1280x1024.

 Początkowy rozmiar okna dialogowego nie powinien przekraczać 1000 pikseli w wysokości, tak aby pasował do ramki IDE w ramach tego minimalnego rozdzielczości o 96 dpi.

### <a name="high-density-displays"></a>Ekrany o wysokiej gęstości
 Interfejs użytkownika w programie Visual Studio musi dobrze współpracować ze wszystkimi czynnikami skalowania DPI, które są obsługiwane przez system Windows: 150%, 200% i 250%.

## <a name="anti-patterns"></a>Antywzorce
 Program Visual Studio zawiera wiele przykładów interfejsu użytkownika, które są zgodne z naszymi wskazówkami i najlepszymi rozwiązaniami. Aby zapewnić spójność, deweloperzy często są pożyczą od wzorców projektu interfejsu użytkownika produktu, podobnie jak w przypadku ich kompilowania. Chociaż jest to dobre podejście, które pomaga nam zapewnić spójność dysków w interakcji z użytkownikiem i projektowaniem wizualizacji, firma Microsoft podejmuje okazję z kilku szczegółów, które nie spełniają naszych wytycznych ze względu na ograniczenia dotyczące harmonogramu lub priorytetyzację wad. W takich przypadkach nie chcemy, aby zespoły skopiowali jeden z tych "antywzorców", ponieważ w środowisku programu Visual Studio są one spójne lub niespójny interfejs użytkownika.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Wymagane pola/ustawienia domyślnie wyświetlane w stanie błędu

#### <a name="feature-team-goals"></a>Cele zespołu funkcji

- Ostrzegaj użytkowników, że dodały element, który musi być skonfigurowany.

- Narysuj uwagę użytkownika na obszary, które wymagają danych wejściowych.

#### <a name="anti-pattern-solution"></a>Rozwiązanie antywzorcowe
 Zaraz po zainicjowaniu akcji przez użytkownika i przed ukończeniem zadania natychmiast Umieść ikony krytyczne-Zatrzymaj obok obszarów, które wymagają konfiguracji.

#### <a name="example-manifest-designer-declarations"></a>Przykład: deklaracje projektanta manifestu
 Dodanie deklaracji do listy natychmiast umieszcza ją w stanie błędu, co zachowuje się, dopóki użytkownik nie ustawi wymaganych właściwości.

 W takim przypadku istnieje dodatkowy problem, ponieważ ikona użyta dla alertu zawiera znak "x", dlatego nie można użyć typowej ikony usuwania. W związku z tym interfejs użytkownika używa przycisku Usuń, clunky formant.

 ![Wzorzec&#45;deklaracji błędu projektanta manifestu](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti — wzorzec")

 **Domyślnie umieszczanie interfejsu użytkownika w stanie błędu jest niezgodne ze standardem programu Visual Studio.**

#### <a name="alternatives"></a>Alternatywy
 Znacznie lepszym rozwiązaniem tego problemu będzie:

- Zezwalaj użytkownikowi na dodawanie deklaracji bez ostrzeżenia, a następnie natychmiast Przenieś, aby ustawić właściwości dla elementu.

- Dodaj ikonę ostrzeżenia (Złoty Trójkąt), gdy fokus jest przenoszony z elementu, na przykład w celu dodania kolejnej deklaracji do listy lub próba zmiany kart w projektancie.

- Jeśli użytkownik spróbuje zmienić karty przed ustawieniem właściwości w dowolnych deklaracjach, w oknie dialogowym wyjaśniono, że aplikacja nie będzie kompilować (lub nie ma wpływu) do momentu rozwiązania ostrzeżeń. Jeśli Użytkownik odrzuci okno dialogowe i zmieni karty, wówczas ikona (krytyczna lub ostrzegawcza) zostanie dodana do karty deklaracje.

### <a name="forcing-the-user-to-read-text-before-dismissing-ui"></a>Wymuszanie odczytu przez użytkownika tekstu przed odinstalowaniem interfejsu użytkownika

#### <a name="feature-team-goals"></a>Cele zespołu funkcji
 Nie Zezwalaj użytkownikowi na odrzucanie interfejsu użytkownika bez uprzedniego wyświetlenia tekstu wyjaśnienia.

#### <a name="anti-pattern"></a>Antywzorzec
 Zespół Wstawiający linki wideo do różnych miejsc w interfejsie użytkownika programu VS zadecyduje o wspólnym wzorcu przycisku zamknięcia X i wyjaśnień etykietki narzędzia zgodnie z opisem w obszarze środowiska

 ![Tekst objaśnienia&#45;wzorzec &#45; nieprawidłowy](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")

 **Nieprawidłowe: wymuszanie odczytywania przez użytkownika tekstu wyjaśniającego przed odinstalowaniem interfejsu użytkownika w programie Visual Studio.**

#### <a name="result"></a>Wynik
 Zamiast prostego przycisku zamknięcia (jednego kliknięcia), użytkownik musi użyć dwóch kliknięć, aby po prostu odrzucić interfejs użytkownika w każdym miejscu, w którym pojawiają się łącza wideo.

#### <a name="alternatives"></a>Alternatywy
 W przypadku poprawnego projektu w tej sytuacji należy przestrzegać wzorca wspólnego dla programu Internet Explorer, pakietu Office i programu Visual Studio: po aktywowaniu użytkownik zobaczy opis etykietki narzędzia, a jednym kliknięciem ukrywa interfejs użytkownika.

 ![Tekst objaśnienia&#45;wzorzec &#45; prawidłowy](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti-Pattern-Correct")

 **Poprawne: zgodnie z założeniami, linki wideo powinny wyświetlać etykietkę narzędzia z dodatkowymi informacjami o aktywowaniu, a kliknięcie "X" powinno odrzucić komunikat bez potrzeby dalszej interakcji.**

### <a name="using-command-bars-for-settings"></a>Używanie pasków poleceń dla ustawień
 ![Pasek poleceń&#45;wzorzec &#45; rysunek A](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-wzór-rysunek")

 **Ilustracja A: pasek poleceń Antywzorzec**

 **Ilustracja A** reprezentuje ten Antywzorzec: umieszczenie ustawienia poniżej przycisku polecenia, który dotyczy więcej niż tylko polecenie. W tym szkicie znajdują się polecenia oprócz debugowania, takie jak widok w przeglądarce, uruchamianie bez debugowania i wkroczenie do, który będzie uwzględniać wybrane ustawienie.

 ![Pasek poleceń&#45;wzorzec &#45; Rysunek B](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti — wzorzec FigureB")

 **Rysunek B: lepszy, ale nadal pasek poleceń Antywzorzec**

 Nieco lepsza, ale nadal niepożądane, umieszcza ustawienia tego typu na paskach narzędzi, jak pokazano na **rysunku B**. Gdy przyciski podziału podzielą się mniej miejsca i w związku z tym są ulepszane przez listy rozwijane, oba projekty nadal korzystają z paska narzędzi, aby podwyższyć poziom, który nie jest w rzeczywistości poleceniem.

 ![Pasek poleceń&#45;wzorzec &#45; rysunek C](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti — wzorzec FigureC")

 **Rysunek C: Popraw użycie wzorca paska poleceń programu Visual Studio**

 Na **rysunku C**ustawienie jest powiązane z serią poleceń. Nie ma ustawionego ustawienia globalnego i przełączamy się między czterema poleceniami. Jest to jedyną sytuacją, w której polecenia na pasku narzędzi są akceptowalne.

### <a name="control-anti-patterns"></a>Kontrolowanie antywzorców
 Niektóre antyki są po prostu nieprawidłowe użycie lub prezentacja kontrolki lub grupy kontrolek.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Podkreślenie użyte jako etykieta grupy, a nie hiperłącze
 Tekst podkreślony powinien być używany tylko w przypadku hiperłączy.

 **Ściągaln**

 ![Podkreślanie&#45;wzorca w etykietach grup](../../extensibility/ux-guidelines/media/0102-g-grouplabelincorrect.png "0102 — g_GroupLabelIncorrect")

 **Niepodkreślony tekst, który nie jest hiperłączem, to Antywzorzec programu Visual Studio.**

 **Aukcj**

 ![W etykietach grup &#40;poprawna&#41;Podkreślaj&#45;](../../extensibility/ux-guidelines/media/0102-h-grouplabelcorrect.png "0102 — h_GroupLabelCorrect")

 **Prawidłowo nakrój stylu tekst niebędący hiperłączem jest wyświetlany jako nieumieszczony w czcionce środowiska.**

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Kliknięcie pola wyboru powoduje wyświetlenie okna dialogowego
 Kliknięcie pola wyboru "Włącz Pulpit zdalny dla wszystkich ról" w Kreatorze "Opublikuj aplikację systemu Windows Azure" spowoduje natychmiastowe wyświetlenie okna dialogowego, które jest niezgodne z Visual Studio. Ponadto pole wyboru nie wypełnia pola wyboru po zaznaczeniu, inne interakcje.

 ![Pole wyboru&#45;w trybie&#45;wzorzec](../../extensibility/ux-guidelines/media/0102-i-checkboxpopup.png "0102 — i_CheckboxPopup")

 **Wyświetlenie okna dialogowego po kliknięciu pola wyboru jest antywzorcem programu Visual Studio.**

### <a name="hyperlink-anti-patterns"></a>Antywzorce hiperlinków
 Poniższy przykład zawiera dwa antywzorce.

1. Kolor pierwszego planu w trybie czerwony przy aktywowaniu oznacza, że nie jest używany prawidłowy, udostępniony przez usługę czcionki.

2. "Dowiedz się więcej" nie jest odpowiednim tekstem dla linku do tematu koncepcyjnego. Celem użytkownika jest, aby nie dowiedzieć się więcej, rozumiesz konsekwencje ich wyboru.

   ![Wzorce anty&#45;hiperlinków](../../extensibility/ux-guidelines/media/0102-j-hyperlinkincorrect.png "0102 — j_HyperlinkIncorrect")

   **Ignorowanie usługi Color i użycie opcji "Dowiedz się więcej" dla hiperłączy to antywzorce programu Visual Studio.**

   **Lepsze rozwiązanie:** Zaproponuj pytanie, którego użytkownik będzie pytał, klikając link.

- Jak działają usługi systemu Windows Azure?

- Kiedy jest potrzebny projekt Mobile Services platformy Microsoft Azure?

#### <a name="using-click-here-for-links"></a>Używanie opcji "kliknij tutaj" dla linków
 Hiperłącza powinny być autoskryptowe. Jest to Antywzorzec do użycia "kliknij tutaj" lub dowolnej podobnej zmiany.

 **Złe:** "Kliknij tutaj, aby uzyskać instrukcje dotyczące sposobu tworzenia nowego projektu".

 **Dobre:** "Jak mogę utworzyć nowy projekt?"
