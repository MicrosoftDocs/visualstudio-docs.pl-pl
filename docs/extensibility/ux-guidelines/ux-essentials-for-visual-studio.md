---
title: Podstawowa ochrona środowiska użytkownika dla programu Visual Studio | Microsoft Docs
description: Zapoznaj się z najlepszymi rozwiązaniami dotyczącymi obsługi nowych funkcji dla programu Visual Studio, w tym wiedzą o rozdzielczości ekranu.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ce44b9234465af6bf52ce8baa0e60e641e845d3c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105052674"
---
# <a name="ux-essentials-for-visual-studio"></a>Podstawy środowiska użytkownika dla programu Visual Studio

## <a name="best-practices"></a>Najlepsze rozwiązania

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. być spójne w środowisku programu Visual Studio.

- Obserwuj istniejące [wzorce interakcji](interaction-patterns-for-visual-studio.md) w powłoce.

- Projektuj funkcje, które mają być zgodne z językiem wizualnym powłoki i [wymaganiami craftsmanship](evaluation-tools-for-visual-studio.md).

- Użyj udostępnionych poleceń i kontrolek, gdy istnieją.

- Zapoznaj się z hierarchią programu Visual Studio i sposobem ustalania kontekstu i dysków interfejsu użytkownika.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Użyj usługi środowiska dla czcionek i kolorów.

- Interfejs użytkownika powinien uwzględniać bieżące ustawienie [czcionki środowiska](fonts-and-formatting-for-visual-studio.md) , chyba że zostanie uwidocznione na potrzeby dostosowywania na stronie czcionki i kolory w oknie dialogowym Opcje.

- Elementy interfejsu użytkownika muszą używać [usługi VSColor](colors-and-styling-for-visual-studio.md)przy użyciu tokenów środowiska udostępnionego lub tokenów specyficznych dla funkcji.

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

- Minimalna rozdzielczość dla programu Visual Studio 2015 to **1280x720**. Oznacza to, *że można korzystać z programu* Visual Studio w tym rozwiązaniu, chociaż może to nie być optymalne środowisko użytkownika. Nie ma gwarancji, że wszystkie aspekty będą użyteczne w rozdzielczościach mniejszych niż 1280x720.

- Docelowa rozdzielczość dla programu Visual Studio to **1366x768**. Jest to najniższa rozdzielczość, w której firma Microsoft gwarantuje *dobre* środowisko użytkownika.

- Początkowa wysokość okna dialogowego powinna być **mniejsza niż 700 pikseli**, więc pasuje do minimalnej rozdzielczości ramki IDE o 96 dpi.

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

 W takim przypadku istnieje dodatkowy problem, ponieważ ikona użyta dla alertu zawiera &times; ikonę "", dlatego nie można użyć typowej ikony usuwania. W związku z tym interfejs użytkownika używa przycisku Usuń, clunky formant.

 ![Domyślnie umieszczanie interfejsu użytkownika w stanie błędu jest niezgodne ze standardem programu Visual Studio.](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti — wzorzec")<br />Domyślnie umieszczanie interfejsu użytkownika w stanie błędu jest niezgodne ze standardem programu Visual Studio.

#### <a name="alternatives"></a>Alternatywy

Lepszym rozwiązaniem tego problemu jest:

- Zezwalaj użytkownikowi na dodawanie deklaracji bez ostrzeżenia, a następnie natychmiast Przenieś, aby ustawić właściwości dla elementu.

- Dodaj ikonę ostrzeżenia (Złoty Trójkąt), gdy fokus jest przenoszony z elementu, na przykład w celu dodania kolejnej deklaracji do listy lub próba zmiany kart w projektancie.

- Jeśli użytkownik spróbuje zmienić karty przed ustawieniem właściwości w dowolnych deklaracjach, w oknie dialogowym wyjaśniono, że aplikacja nie będzie kompilować (lub nie ma wpływu) do momentu rozwiązania ostrzeżeń. Jeśli Użytkownik odrzuci okno dialogowe i zmieni karty, wówczas ikona (krytyczna lub ostrzegawcza) zostanie dodana do karty deklaracje.

### <a name="multiple-clicks-to-dismiss-ui"></a>Wielokrotne kliknięcia do odrzucania interfejsu użytkownika

#### <a name="feature-team-goals"></a>Cele zespołu funkcji
 Nie Zezwalaj użytkownikowi na odrzucanie interfejsu użytkownika bez uprzedniego wyświetlenia tekstu wyjaśnienia.

#### <a name="anti-pattern"></a>Antywzorzec
 Zespół Wstawiający linki wideo do różnych miejsc w interfejsie użytkownika programu VS decyduje o wspólnym wzorcu &times; przycisku "Zamknij" i porady dotyczącej etykietki narzędzia zgodnie z opisem w obszarze środowiska

#### <a name="example-video-links-in-team-explorer"></a>Przykład: linki wideo w Team Explorer
Wymuszanie odczytywania przez użytkownika tekstu wyjaśniającego przed odinstalowaniem interfejsu użytkownika jest antywzorców w programie Visual Studio. Prawidłowo zaprojektowane, linki wideo powinny wyświetlać etykietkę narzędzia z dodatkowymi informacjami na temat aktywowania, a kliknięcie " &times; " powinno odrzucić komunikat bez potrzeby dalszej interakcji.

 ![Tekst objaśnienia&#45;wzorzec &#45; nieprawidłowy](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />Nieprawidłowy wzorzec linku wideo

Zamiast prostego przycisku zamknięcia (jednego kliknięcia), użytkownik musi użyć dwóch kliknięć, aby po prostu odrzucić interfejs użytkownika w każdym miejscu, w którym pojawiają się łącza wideo.

Prawidłowym projektem w tej sytuacji jest przestrzeganie wzorca wspólnego dla programu Internet Explorer, pakietu Office i programu Visual Studio: po aktywowaniu użytkownik może zobaczyć opis etykietki narzędzia, a jednym kliknięciem spowoduje ukrycie interfejsu użytkownika.

 ![Tekst objaśnienia&#45;wzorzec &#45; prawidłowy](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti-Pattern-Correct")<br />Poprawny wzorzec linku wideo

### <a name="using-command-bars-for-settings"></a>Używanie pasków poleceń dla ustawień

**Ilustracja A** reprezentuje ten Antywzorzec: umieszczenie ustawienia poniżej przycisku polecenia, który dotyczy więcej niż tylko polecenie. W tym szkicie znajdują się polecenia oprócz debugowania, takie jak widok w przeglądarce, uruchamianie bez debugowania i wkroczenie do, który będzie uwzględniać wybrane ustawienie.

![Ilustracja A: pasek poleceń Antywzorzec](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-wzór-rysunek")<br />Ilustracja A: pasek poleceń Antywzorzec

Nieco lepsza, ale nadal niepożądane, umieszcza ustawienia tego typu na paskach narzędzi, jak pokazano na **rysunku B**. Gdy przyciski podziału podzielą się mniej miejsca i w związku z tym są ulepszane przez listy rozwijane, oba projekty nadal korzystają z paska narzędzi, aby podwyższyć poziom, który nie jest w rzeczywistości poleceniem.

![Rysunek B: lepszy, ale nadal pasek poleceń Antywzorzec](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti — wzorzec FigureB")<br />Rysunek B: lepszy, ale nadal pasek poleceń Antywzorzec

W poprawnym podejściu pokazanym na **rysunku C** ustawienie jest powiązane z serią poleceń. Nie ma ustawionego ustawienia globalnego i przełączamy się między czterema poleceniami. Jest to jedyną sytuacją, w której polecenia na pasku narzędzi są akceptowalne.

![Rysunek C: Popraw użycie wzorca paska poleceń programu Visual Studio](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti — wzorzec FigureC")<br />Rysunek C: Popraw użycie wzorca paska poleceń programu Visual Studio

### <a name="control-anti-patterns"></a>Kontrolowanie antywzorców
 Niektóre antyki są po prostu nieprawidłowe użycie lub prezentacja kontrolki lub grupy kontrolek.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Podkreślenie użyte jako etykieta grupy, a nie hiperłącze
 Tekst podkreślony powinien być używany tylko w przypadku hiperłączy.

 **Ściągaln**\
 ![Niepodkreślony tekst, który nie jest hiperłączem, to Antywzorzec programu Visual Studio.](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102 — g_GroupLabelIncorrect")<br />Niepodkreślony tekst, który nie jest hiperłączem, to Antywzorzec programu Visual Studio.

 **Aukcj**\
 ![Prawidłowo nakrój stylu tekst niebędący hiperłączem jest wyświetlany jako nieumieszczony w czcionce środowiska.](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102 — h_GroupLabelCorrect")<br />Prawidłowo nakrój stylu tekst niebędący hiperłączem jest wyświetlany jako nieumieszczony w czcionce środowiska.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Kliknięcie pola wyboru powoduje wyświetlenie okna dialogowego
 Kliknięcie pola wyboru "Włącz Pulpit zdalny dla wszystkich ról" w Kreatorze "Opublikuj aplikację systemu Windows Azure" spowoduje natychmiastowe wyświetlenie okna dialogowego, które jest niezgodne z Visual Studio. Ponadto pole wyboru nie wypełnia pola wyboru po zaznaczeniu, inne interakcje.

 ![Wyświetlenie okna dialogowego po kliknięciu pola wyboru jest antywzorcem programu Visual Studio.](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102 — i_CheckboxPopup")<br />Wyświetlenie okna dialogowego po kliknięciu pola wyboru jest antywzorcem programu Visual Studio.

### <a name="hyperlink-anti-patterns"></a>Antywzorce hiperlinków
 Poniższy przykład zawiera dwa antywzorce:

1. Kolor pierwszego planu w trybie czerwony przy aktywowaniu oznacza, że nie jest używany prawidłowy, udostępniony przez usługę czcionki.

2. "Dowiedz się więcej" nie jest odpowiednim tekstem dla linku do tematu koncepcyjnego. Celem użytkownika jest, aby nie dowiedzieć się więcej, rozumiesz konsekwencje ich wyboru.

   ![Ignorowanie usługi Color i użycie opcji "Dowiedz się więcej" dla hiperłączy to antywzorce programu Visual Studio.](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102 — j_HyperlinkIncorrect")<br />Ignorowanie usługi Color i użycie opcji "Dowiedz się więcej" dla hiperłączy to antywzorce programu Visual Studio.

**Lepsze rozwiązanie:** Zaproponuj pytanie, którego użytkownik będzie pytał, klikając link. Na przykład:

- Jak działają usługi systemu Windows Azure?

- Kiedy jest potrzebny projekt Mobile Services platformy Microsoft Azure?

#### <a name="using-click-here-for-links"></a>Używanie opcji "kliknij tutaj" dla linków
 Hiperłącza powinny być autoskryptowe. Jest to Antywzorzec do użycia "kliknij tutaj" lub dowolnej podobnej zmiany.

 **Złe:** "Kliknij tutaj, aby uzyskać instrukcje dotyczące sposobu tworzenia nowego projektu".

 **Dobre:** "Jak mogę utworzyć nowy projekt?"
