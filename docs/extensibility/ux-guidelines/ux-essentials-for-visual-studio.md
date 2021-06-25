---
title: Podstawowe informacje dotyczące środowiska użytkownika Visual Studio | Microsoft Docs
description: Zapoznaj się z tymi najlepszymi rozwiązaniami w zakresie obsługi użytkownika dla nowych funkcji, które opracowujesz dla Visual Studio, w tym znajomość rozpoznawania ekranu.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 74b27e87e6f16130573ef6671286501f77e44352
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899423"
---
# <a name="ux-essentials-for-visual-studio"></a>Podstawy środowiska użytkownika dla programu Visual Studio

## <a name="best-practices"></a>Najlepsze rozwiązania

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Należy zapewnić spójność w Visual Studio środowisku.

- Postępuj zgodnie z [istniejącymi wzorcami interakcji](interaction-patterns-for-visual-studio.md) w obrębie powłoki.

- Zaprojektuj funkcje tak, aby były zgodne z wymaganiami powłoki i językiem [wizualnym.](evaluation-tools-for-visual-studio.md)

- Użyj udostępnionych poleceń i kontrolek, gdy istnieją.

- Poznaj hierarchię Visual Studio oraz sposób ustanawiania kontekstu i kieruje interfejsem użytkownika.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Użyj usługi środowiska dla czcionek i kolorów.

- Interfejs użytkownika powinien przestrzegać bieżącego [ustawienia czcionki środowiska,](fonts-and-formatting-for-visual-studio.md) chyba że zostanie ono ujawnione do dostosowania na stronie Czcionki i kolory w oknie dialogowym Opcje.

- Elementy interfejsu użytkownika muszą używać [usługi VSColor Service](colors-and-styling-for-visual-studio.md)przy użyciu tokenów środowiska udostępnionego lub tokenów specyficznych dla funkcji.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Zapewnianie spójności wszystkich obrazów z nowym stylem programu VS.

- Postępuj Visual Studio projektowania ikon, symboli i innych grafik.

- Nie umieszczaj tekstu w elementach graficznych.

### <a name="4-design-from-a-user-centric-perspective"></a>4. Projektuj z perspektywy użytkownika.

- Utwórz przepływ zadań przed poszczególnymi jego cechami.

- Zapoznaj się ze swoimi użytkownikami i ujmij je jawnie w specyfikacji.

- Podczas przeglądania interfejsu użytkownika oceń kompletne środowisko oraz szczegóły.

- Zaprojektuj interfejs użytkownika tak, aby pozostał funkcjonalny i atrakcyjny niezależnie od ustawieniach regionalnych lub języka.

## <a name="screen-resolution"></a>Rozdzielczość ekranu

### <a name="minimum-resolution"></a>Minimalna rozdzielczość

- Minimalna rozdzielczość dla Visual Studio 2015 to **1280x720.** Oznacza to, że *możliwe jest użycie Visual Studio* w tej rozdzielczości, chociaż może to nie być optymalne środowisko użytkownika. Nie ma gwarancji, że wszystkie aspekty będą dostępne w rozdzielczości niższej niż 1280 x 720.

- Rozdzielczość docelowa dla Visual Studio to **1366x768.** Jest to najniższa rozdzielczość, przy której mamy *obietnicę dobrego interfejsu* użytkownika.

- Początkowa wysokość okna dialogowego powinna być mniejsza **niż 700** pikseli, więc mieści się w minimalnej rozdzielczości ramki IDE przy rozdzielczości 96 dpi.

### <a name="high-density-displays"></a>Ekrany o wysokiej gęstości
 Interfejs użytkownika w Visual Studio musi działać dobrze we wszystkich czynnikach skalowania DPI, które system Windows obsługuje po instalacji: 150%, 200% i 250%.

## <a name="anti-patterns"></a>Antyw wzorcach
 Visual Studio zawiera wiele przykładów interfejsu użytkownika, które są zgodne z naszymi wytycznymi i najlepszymi rozwiązaniami. Aby zapewnić spójność, deweloperzy często zapożyczają się na wzorcach projektowych interfejsu użytkownika produktu podobnych do budowania. Chociaż jest to dobre podejście, które pomaga nam zapewnić spójność interakcji z użytkownikami i projektowania wizualnego, w niektórych przypadkach używamy funkcji wysyłkowych z kilkoma szczegółami, które nie spełniają naszych wytycznych ze względu na ograniczenia harmonogramu lub priorytetyzację wad. W takich przypadkach nie chcemy, aby zespoły kopiowały jeden z tych "wzorców antywmysowych", ponieważ wyeksymilują one zły lub niespójny interfejs użytkownika w Visual Studio środowisku.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Wymagane pola/ustawienia domyślnie wyświetlane w stanie błędu

#### <a name="feature-team-goals"></a>Cele zespołu funkcji

- Ostrzegaj użytkowników, że dodali element, który należy skonfigurować.

- Zwróć uwagę użytkownika na obszary, które wymagają danych wejściowych.

#### <a name="anti-pattern-solution"></a>Rozwiązanie antyw wzorzec
 Natychmiast po zainicjowaniu akcji przez użytkownika i przed ukończeniem zadania natychmiast umieść ikony zatrzymania krytycznego obok obszarów, które wymagają konfiguracji.

#### <a name="example-manifest-designer-declarations"></a>Przykład: deklaracje projektanta manifestu
 Dodanie deklaracji do listy natychmiast umieszcza ją w stanie błędu, który będzie się powtarzać do momentu ustawienia wymaganych właściwości przez użytkownika.

 W tym przypadku jest to dodatkowa kwestią, ponieważ ikona używana dla alertu zawiera ikonę " ", więc nie można użyć wspólnej ikony usuwania &times; obok niego. W związku z tym interfejs użytkownika używa przycisku Usuń, bardziej clunky formantu.

 ![Domyślne umieszczenie interfejsu użytkownika w stanie błędu jest Visual Studio antyw wzorzec.](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-pattern")<br />Domyślne umieszczenie interfejsu użytkownika w stanie błędu jest Visual Studio antyw wzorzec.

#### <a name="alternatives"></a>Alternatywy

Lepszym rozwiązaniem tego problemu jest:

- Zezwala użytkownikowi na dodawanie deklaracji bez ostrzeżenia, a następnie natychmiastowe przenoszenie w celu ustawienia właściwości elementu.

- Dodaj ikonę ostrzeżenia (złoty trójkąt), gdy fokus zostanie przeniesiony z elementu, na przykład w celu dodania kolejnej deklaracji do listy lub próby zmiany kart w projektancie.

- Jeśli użytkownik spróbuje zmienić karty przed ustawieniem właściwości w dowolnej deklaracji, w oknie dialogowym pojawi się okno dialogowe z wyjaśnieniem, że aplikacja nie zostanie skompilowana (ani nie będzie to miało żadnego wpływu) do momentu rozwiązania ostrzeżeń. Jeśli użytkownik mimo to odrzuci okno dialogowe i zmieni karty, do karty Deklaracje zostanie dodana ikona (krytyczna lub ostrzeżenie).

### <a name="multiple-clicks-to-dismiss-ui"></a>Wiele kliknięć w celu odrzucania interfejsu użytkownika

#### <a name="feature-team-goals"></a>Cele zespołu funkcji
 Nie zezwalaj użytkownikowi na odrzucanie interfejsu użytkownika bez wcześniejszego zobaczenia tekstu wyjaśnienia.

#### <a name="anti-pattern"></a>Antyw wzorzec
 Zespół wstawiający linki wideo w różnych miejscach w interfejsie użytkownika programu VS zdecydował się na wspólny wzorzec "Przycisk zamykania i wyjaśnienie etykietki narzędzia określone przez interfejs użytkownika, a zamiast tego zaimplementował menu rozwijane i link "Nie pokazuj &times; ponownie".

#### <a name="example-video-links-in-team-explorer"></a>Przykład: linki wideo w Team Explorer
Wymuś na użytkowniku przeczytanie tekstu objaśnienia przed odrzuceniem interfejsu użytkownika jest antyw wzorzecem w Visual Studio. Poprawnie zaprojektowane linki wideo powinny wyświetlać etykietkę narzędzia z dodatkowymi informacjami po najechaniu kursorem, a kliknięcie przycisku " " powinno odrzucić komunikat bez konieczności &times; dalszej interakcji.

 ![Wzorzec ochrony tekstu objaśnienia&#45;jest &#45; nieprawidłowy](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />Nieprawidłowy wzorzec linku wideo

Zamiast prostego przycisku zamykania (jednym kliknięciem) użytkownik musi użyć dwóch kliknięć, aby po prostu odrzucić interfejs użytkownika w każdym miejscu, w którym są wyświetlane linki wideo.

Prawidłowy projekt w tej sytuacji jest zgodne ze wzorcem wspólnym dla platform Internet Explorer, Office i Visual Studio: po umieszczeniu wskaźnika myszy użytkownik może zobaczyć opis etykietki narzędzia, a jedno kliknięcie ukrywa interfejs użytkownika.

 ![Wzorzec ochrony tekstu objaśnienia&#45;jest &#45; prawidłowy](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Tekst objaśnieniaanti-pattern-correct")<br />Poprawny wzorzec linku wideo

### <a name="using-command-bars-for-settings"></a>Używanie pasków poleceń dla ustawień

**Rysunek A** przedstawia ten wzorzec: umieszczenie ustawienia poniżej przycisku polecenia, który ma zastosowanie nie tylko do polecenia. W tym szkicu istnieją polecenia oprócz polecenia Rozpocznij debugowanie — takie jak Wyświetl w przeglądarce, Uruchom bez debugowania i Krok do — które będą uwzględniać wybrane ustawienie.

![Rysunek A. Antyw wzorzec paska poleceń](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-pattern-FigureA")<br />Rysunek A. Antyw wzorzec paska poleceń

Nieco lepiej, ale nadal niepożądane, jest umieszczanie ustawień tego typu na paskach narzędzi, jak pokazano na rysunku **B.** Chociaż przyciski podziału mają mniej miejsca i w związku z tym są ulepszeniem listy rozwijanej, obie projekty nadal promują coś, co nie jest poleceniem, przy użyciu paska narzędzi.

![Rysunek B. Lepsza, ale nadal antyw wzorzec paska poleceń](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-pattern-FigureB")<br />Rysunek B. Lepsza, ale nadal antyw wzorzec paska poleceń

W poprawnym podejściu pokazanym na rysunku **C** to ustawienie jest powiązane z serią poleceń. Nie jest ustawiane żadne ustawienie globalne i przełączamy się między czterema poleceniami. Jest to jedyna sytuacja, w której polecenia na pasku narzędzi są dopuszczalne.

![Rysunek C. Poprawne użycie Visual Studio wzorca paska poleceń](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-pattern-FigureC")<br />Rysunek C. Poprawne użycie Visual Studio wzorca paska poleceń

### <a name="control-anti-patterns"></a>Antywłaściwki kontrolek
 Niektóre antywłaściwki to po prostu niepoprawne użycie lub prezentacja kontrolki lub grupy kontrolek.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Underlining używany jako etykieta grupy, a nie hiperlink
 Tekst podliniowy powinien być używany tylko w przypadku hiperlinków.

 **Bad:**\
 ![Podkreślony tekst, który nie jest hiperlinkiem, Visual Studio antyw wzorzec.](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-g_GroupLabelIncorrect")<br />Podkreślony tekst, który nie jest hiperlinkiem, Visual Studio antyw wzorzec.

 **Dobry:**\
 ![Tekst bez hiperlinku ma prawidłowy styl i jest wyświetlany bez wstawionej czcionki środowiska.](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-h_GroupLabelCorrect")<br />Tekst bez hiperlinku ma prawidłowy styl i jest wyświetlany bez wstawionej czcionki środowiska.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Kliknięcie pola wyboru powoduje kliknięcie wyskakującego okna dialogowego
 Kliknięcie pola wyboru "Włącz Pulpit zdalny dla wszystkich ról" w kreatorze "Publikowanie aplikacji platformy Microsoft Azure" natychmiast pojawia się wyskakujące okno dialogowe, Visual Studio antyw wzorzec. Ponadto pole wyboru nie jest wypełniane polem wyboru po zaznaczeniu, innym antywęzowym wzorcem interakcji.

 ![Okno dialogowe po kliknięciu pola wyboru jest Visual Studio antyw wzorzec.](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-i_CheckboxPopup")<br />Okno dialogowe po kliknięciu pola wyboru jest Visual Studio antyw wzorzec.

### <a name="hyperlink-anti-patterns"></a>Antyw wzorcach hiperlinków
 Poniższy przykład zawiera dwa antyw wzorcach:

1. Włączenie koloru czerwonego na pierwszym planie oznacza, że poprawny kolor udostępniony z usługi czcionek nie jest używany.

2. "Dowiedz się więcej" nie jest odpowiednim tekstem linku do tematu koncepcyjnego. Celem użytkownika nie jest nauka więcej, ale zrozumienie konsekwencji wybranego przez niego wyboru.

   ![Ignorowanie usługi kolorów i używanie funkcji "Dowiedz się więcej" dla hiperlinków Visual Studio antyw wzorcach.](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")<br />Ignorowanie usługi kolorów i używanie funkcji "Dowiedz się więcej" dla hiperlinków Visual Studio antywłaściwkami.

**Lepsze rozwiązanie:** Zadaj pytanie, które użytkownik zadaje, klikając link. Na przykład:

- Jak działają usługi platformy Microsoft Azure?

- Kiedy muszę mieć projekt usługi Windows Azure Mobile Services?

#### <a name="using-click-here-for-links"></a>Użycie linku "Kliknij tutaj"
 Hiperlinki powinny być samoopisowe. Używanie typu "Kliknij tutaj" lub dowolnej podobnej odmiany jest antyw wzorzecem.

 **Zły:** "Kliknij tutaj, aby uzyskać instrukcje dotyczące sposobu tworzenia nowego projektu".

 **Dobre:** "Jak mogę utworzyć nowy projekt?"
