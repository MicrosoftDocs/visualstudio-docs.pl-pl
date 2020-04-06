---
title: Ux Essentials dla programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6c329eda477d77ab73be2ad913ac18d67ff3c08
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698330"
---
# <a name="ux-essentials-for-visual-studio"></a>Podstawy środowiska użytkownika dla programu Visual Studio

## <a name="best-practices"></a>Najlepsze rozwiązania

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Bądź spójny w środowisku Visual Studio.

- Postępuj zgodnie z [istniejącymi wzorcami interakcji](interaction-patterns-for-visual-studio.md) w powłoce.

- Funkcje konstrukcyjne, które mają być zgodne z językiem wizualnym i [wymaganiami dotyczącymi rzemiosła powłoki.](evaluation-tools-for-visual-studio.md)

- Użyj udostępnionych poleceń i formantów, gdy istnieją.

- Zrozumieć hierarchii programu Visual Studio i jak ustanawia kontekst i dyski interfejsu użytkownika.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Użyj usługi ochrony środowiska dla czcionek i kolorów.

- Interfejs użytkownika powinien być zgodny z bieżącym [ustawieniem czcionki środowiska,](fonts-and-formatting-for-visual-studio.md) chyba że jest ono widoczne w celu dostosowania na stronie Czcionki i kolory w oknie dialogowym Opcje.

- Elementy interfejsu użytkownika należy użyć [usługi VSColor](colors-and-styling-for-visual-studio.md), przy użyciu tokenów środowiska udostępnionego lub tokenów specyficznych dla funkcji.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Upewnij się, że wszystkie obrazy są zgodne z nowym stylem VS.

- Postępuj zgodnie z zasadami projektowania programu Visual Studio dla ikon, glifów i innych grafik.

- Nie umieszczaj tekstu w elementach graficznych.

### <a name="4-design-from-a-user-centric-perspective"></a>4. Projektowanie z punktu widzenia zorientowanego na użytkownika.

- Utwórz przepływ zadań przed poszczególnymi elementami w nim.

- Zapoznaj się z użytkownikami i spraw, aby ta wiedza była wyraźnie wiedzna w specyfikacji.

- Podczas przeglądania interfejsu użytkownika, należy ocenić pełne środowisko, jak również szczegóły.

- Zaprojektuj swój interfejs użytkownika tak, aby pozostał funkcjonalny i atrakcyjny niezależnie od ustawień regionalnych lub językowych.

## <a name="screen-resolution"></a>Rozdzielczość ekranu

### <a name="minimum-resolution"></a>Minimalna rozdzielczość

- Minimalna rozdzielczość programu Visual Studio 2015 to **1280x720**. Oznacza to, że jest *możliwe* użycie programu Visual Studio w tej rozdzielczości, chociaż może nie być optymalne środowisko użytkownika. Nie ma gwarancji, że wszystkie aspekty będą użyteczne w rozdzielczościach niższych niż 1280x720.

- Rozdzielczość docelowa programu Visual Studio to **1366x768**. Jest to najniższa rozdzielczość, przy której obiecujemy *dobre* wrażenia użytkownika.

- Początkowa wysokość okna dialogowego powinna być **mniejsza niż 700 pikseli,** więc mieści się w minimalnej rozdzielczości ramki IDE przy 96 dpi.

### <a name="high-density-displays"></a>Wyświetlacze o dużej gęstości
 Interfejs użytkownika w programie Visual Studio musi działać dobrze we wszystkich współczynnikach skalowania DPI, które system Windows obsługuje po wyjęciu z pudełka: 150%, 200% i 250%.

## <a name="anti-patterns"></a>Anty-wzory
 Visual Studio zawiera wiele przykładów interfejsu użytkownika, które są zgodne z naszymi wskazówkami i najlepszymi rozwiązaniami. Aby być konsekwentnym, deweloperzy często pożyczają od wzorców projektowania interfejsu użytkownika produktu podobnych do tego, co budują. Chociaż jest to dobre podejście, które pomaga nam zwiększyć spójność interakcji z użytkownikiem i projektowanie wizualne, czasami wysyłamy funkcje z kilkoma szczegółami, które nie spełniają naszych wytycznych ze względu na ograniczenia harmonogramu lub priorytety wada. W takich przypadkach nie chcemy zespołów do kopiowania jednego z tych "wzorców anty wzorców", ponieważ mnożą one zły lub niespójny interfejs użytkownika w środowisku programu Visual Studio.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Wymagane pola/ustawienia wyświetlane domyślnie w stanie błędu

#### <a name="feature-team-goals"></a>Cechy cele zespołu

- Ostrzegaj użytkowników, że dodali element, który musi być skonfigurowany.

- Zwróć uwagę użytkownika na obszary, które wymagają danych wejściowych.

#### <a name="anti-pattern-solution"></a>Rozwiązanie antyszwowe
 Jak tylko użytkownik zainicjował akcję i przed zakończeniem zadania, natychmiast umieść ikony zatrzymania krytycznego obok obszarów, które wymagają konfiguracji.

#### <a name="example-manifest-designer-declarations"></a>Przykład: deklaracje projektanta manifestów
 Dodanie deklaracji do listy natychmiast umieszcza go w stanie błędu, który utrzymuje się, dopóki użytkownik nie ustawi wymaganych właściwości.

 W takim przypadku istnieje dodatkowy problem, ponieważ ikona używana&times;dla alertu zawiera ikonę " ", więc nie można użyć ikony usuwania obok niej. W rezultacie interfejs użytkownika używa przycisku Usuń, bardziej niezgrabny kontroli.

 ![Umieszczenie interfejsu użytkownika w stanie błędu domyślnie jest visual studio anti-pattern.](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-pattern Manifest")<br />Umieszczenie interfejsu użytkownika w stanie błędu domyślnie jest visual studio anti-pattern.

#### <a name="alternatives"></a>Alternatywy

Lepszym rozwiązaniem tego problemu jest:

- Zezwalaj użytkownikowi na dodawanie deklaracji bez ostrzeżenia, a następnie natychmiast przenieść, aby ustawić właściwości elementu.

- Dodaj ikonę ostrzeżenia (złoty trójkąt), gdy fokus przesuwa się z elementu, na przykład, aby dodać inną deklarację do listy lub spróbować zmienić karty w projektancie.

- Jeśli użytkownik próbuje zmienić karty przed ustawieniem właściwości na żadnych deklaracji, pop okno dialogowe wyjaśniające, że aplikacja nie będzie budować (lub cokolwiek implikacje) dopóki ostrzeżenia zostaną rozwiązane. Jeśli użytkownik odrzuci okno dialogowe i mimo to zmieni karty, ikona (krytyczne lub ostrzeżenie, w razie potrzeby) zostanie dodana do karty Deklaracje.

### <a name="multiple-clicks-to-dismiss-ui"></a>Wiele kliknięć w celu odrzucenia interfejsu użytkownika

#### <a name="feature-team-goals"></a>Cechy cele zespołu
 Nie zezwalaj użytkownikowi na odrzucenie interfejsu użytkownika bez uprzedniego wyświetlania tekstu objaśnienia.

#### <a name="anti-pattern"></a>Anty-wzór
 Zespół wstawiając łącza wideo do różnych miejsc w interfejsie vs&times;postanowił przeciwko wspólny wzorzec " " przycisk zamknięcia i opis etykietki narzędzia, jak określono przez UX, a zamiast tego zaimplementował rozwijane i "Nie pokazuj ponownie" link.

#### <a name="example-video-links-in-team-explorer"></a>Przykład: łącza wideo w Eksploratorze zespołu
Zmuszanie użytkownika do odczytu tekstu objaśniającego przed odrzuceniem interfejsu użytkownika jest wzorcem antywłasnym w programie Visual Studio. Poprawnie zaprojektowane łącza wideo powinny wyświetlać etykietkę narzędzia z dodatkowymi informacjami po najechaniu kursorem, a kliknięcie przycisku "&times;" powinno odrzucić wiadomość bez konieczności dalszej interakcji.

 ![Tekst wyjaśniający anty&#45;wzór &#45; nieprawidłowy](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Nieprawidłowe użycie wielu błędów")<br />Nieprawidłowy wzór łącza wideo

Zamiast prostego przycisku zamykania (jedno kliknięcie), użytkownik jest zmuszony użyć dwóch kliknięć, aby po prostu odrzucić interfejs użytkownika w każdym miejscu, w które pojawiają się łącza wideo.

Prawidłowy projekt dla tej sytuacji jest zgodne ze wzorcem wspólne dla programu Internet Explorer, Office i Visual Studio: po najechaniu kursorem myszy użytkownik może zobaczyć opis etykietki narzędzia i jedno kliknięcie ukrywa interfejsu użytkownika.

 ![Tekst wyjaśniający anty&#45;wzór &#45; poprawny](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Wyjaśniający tekstanti-wzór-poprawne")<br />Poprawny wzór łącza wideo

### <a name="using-command-bars-for-settings"></a>Używanie pasków poleceń do ustawień

**Rysunek A** reprezentuje ten wzorzec: umieszczenie ustawienia pod przyciskiem polecenia, który odnosi się do więcej niż tylko polecenia. W tym szkicu istnieją polecenia oprócz start debugowania — takie jak Widok w przeglądarce, Start bez debugowania i Krok do — które będą respektować wybrane ustawienie.

![Rysunek A: Anty-wzór paska poleceń](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-wzór-RysunekA")<br />Rysunek A: Anty-wzór paska poleceń

Nieco lepiej, ale nadal niepożądane, jest umieszczenie ustawień tego typu na paskach narzędzi, jak pokazano na **rysunku B**. Podczas gdy przyciski podziału zajmują mniej miejsca i dlatego są ulepszeniem w stosunku do rozwijanych, oba projekty nadal używają paska narzędzi do promowania czegoś, co tak naprawdę nie jest poleceniem.

![Rysunek B: Lepiej, ale nadal pasek poleceń anty-wzór](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-wzór-FigureB")<br />Rysunek B: Lepiej, ale nadal pasek poleceń anty-wzór

W prawidłowym podejściu pokazanym na **rysunku C**ustawienie jest powiązane z serią poleceń. Nie ma ustawienia globalnego i po prostu przełączamy się między czterema poleceniami. Jest to jedyna sytuacja, w której polecenia na pasku narzędzi są dopuszczalne.

![Rysunek C: Prawidłowe użycie wzorca paska poleceń programu Visual Studio](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-wzór-RysunekC")<br />Rysunek C: Prawidłowe użycie wzorca paska poleceń programu Visual Studio

### <a name="control-anti-patterns"></a>Sterowanie anty-wzory
 Niektóre wzorce anty-są po prostu nieprawidłowe użycie lub prezentacja formantu lub grupy formantów.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Podkreślenie używane jako etykieta grupy, a nie hiperłącze
 Tekst podkreślenia powinien być używany tylko w przypadku hiperłączy.

 **Bad:**\
 ![Podkreślony tekst, który nie jest hiperłączem, jest wzorcem antywzorzeszku programu Visual Studio.](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-g_GroupLabelIncorrect")<br />Podkreślony tekst, który nie jest hiperłączem, jest wzorcem antywzorzeszku programu Visual Studio.

 **Dobry:**\
 ![Poprawnie stylizowany tekst niebędący hiperłączem jest wyświetlany w czcionce środowiska bez ozdabiania.](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-h_GroupLabelCorrect")<br />Poprawnie stylizowany tekst niebędący hiperłączem jest wyświetlany w czcionce środowiska bez ozdabiania.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Kliknięcie pola wyboru powoduje wyświetlenie okna dialogowego
 Kliknięcie pola wyboru "Włącz pulpit zdalny dla wszystkich ról" w kreatorze "Publikowanie aplikacji systemu Windows Azure" natychmiast powoduje wyświetlenie wyskakującego okna dialogowego, wzorca antywyszku programu Visual Studio. Ponadto pole wyboru nie wypełnia się polem wyboru po zaznaczeniu, innym anty-wzorcem interakcji.

 ![Wychowując okno dialogowe po kliknięciu pola wyboru jest visual studio anti-pattern.](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-i_CheckboxPopup")<br />Wychowując okno dialogowe po kliknięciu pola wyboru jest visual studio anti-pattern.

### <a name="hyperlink-anti-patterns"></a>Wzorce antyłączowe hiperłącza
 Poniższy przykład zawiera dwa wzorce antywzórowe:

1. Pierwszy plan włączania na czerwono po najechaniu oznacza, że poprawny kolor udostępniony z usługi czcionek nie jest używany.

2. "Dowiedz się więcej" nie jest odpowiednim tekstem dla łącza do tematu koncepcyjnego. Celem użytkownika nie jest, aby dowiedzieć się więcej, to zrozumieć konsekwencje ich wyboru.

   ![Ignorowanie usługi kolorów i za pomocą "Dowiedz się więcej" dla hiperłączy są visual studio wzorce anty.Ignoring the color service and using "Learn more" for hyperlinks are Visual Studio anti-patterns.](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")<br />Ignorowanie usługi kolorów i za pomocą "Dowiedz się więcej" dla hiperłączy są visual studio wzorce anty.Ignoring the color service and using "Learn more" for hyperlinks are Visual Studio anti-patterns.

**Lepsze rozwiązanie:** Zadaj pytanie, które użytkownik zadaje, klikając link. Przykład:

- Jak działają usługi Systemu Windows Azure?

- Kiedy potrzebuję projektu usług Windows Azure Mobile Services?

#### <a name="using-click-here-for-links"></a>Korzystanie z "Kliknij tutaj" dla linków
 Hiperłącza powinny być samookreślone. Jest to anty-wzór do korzystania z "Kliknij tutaj" lub podobnej odmiany.

 **Źle:** "Kliknij tutaj, aby uzyskać instrukcje dotyczące tworzenia nowego projektu."

 **Dobry:** "Jak utworzyć nowy projekt?"
