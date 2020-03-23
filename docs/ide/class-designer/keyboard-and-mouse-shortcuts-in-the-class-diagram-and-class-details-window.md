---
title: Skróty klawiaturowe i myszy dla projektanta klas
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.classdetails.window
helpviewer_keywords:
- class diagrams, keyboard shortcuts
- class diagrams, mouse shortcuts
ms.assetid: c12d8dac-9902-4fde-b721-2a8116da53b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6df4932a1043c984509632951ba67864fefe31ce
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590764"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window"></a>Skróty klawiaturowe i myszy w oknie Diagram klas i Szczegóły klasy

Oprócz myszy można używać klawiatury do wykonywania akcji nawigacyjnych w **projektancie klas** i w oknie **Szczegóły klasy.**

## <a name="use-the-mouse-in-class-designer"></a>Używanie myszy w projektancie klas

Następujące akcje myszy są obsługiwane na diagramach klas:

|Kombinacja myszy|Kontekst|Opis|
| - |-------------|-----------------|
|Kliknij dwukrotnie|elementy kształtu|Otwiera edytor kodu.|
|Kliknij dwukrotnie|Złącze lizaka|Rozwiń / zwiń lizaka.|
|Kliknij dwukrotnie|Etykieta złącza Lizak|Wywołuje polecenie **Pokaż interfejs.**|
|Kółko myszy|Diagram klas|Przewiń w pionie.|
|**Shift** + kółko myszy|Diagram klas|Przewiń w poziomie.|
|**Ctrl** + kółko myszy|Diagram klas|Powiększenia.|
|**Ctrl**+**Shift** + kliknięcie|Diagram klas|Powiększenia.|

## <a name="use-the-mouse-in-the-class-details-window"></a>Użyj myszy w oknie Szczegóły klasy

Za pomocą myszy można zmienić wygląd okna **Szczegóły klasy** i wyświetlane dane w następujący sposób:

- Kliknięcie dowolnej komórki edytowalnej umożliwia edycję zawartości tej komórki. Zmiany są odzwierciedlane we wszystkich miejscach, w których dane są przechowywane lub wyświetlane, w tym w oknie **Właściwości** i w kodzie źródłowym.

- Kliknięcie dowolnej komórki wiersza **powoduje,** że okno Właściwości wyświetla właściwości elementu reprezentowanego przez ten wiersz.

- Aby zmienić szerokość kolumny, przeciągnij granicę po prawej stronie nagłówka kolumny, aż kolumna będzie mieć odpowiednią szerokość.

- Można rozwinąć lub zwinąć przedział lub węzły właściwości, klikając symbole strzałek po lewej stronie wiersza.

- Okno **Szczegóły klasy** oferuje kilka przycisków do tworzenia nowych elementów członkowskich w bieżącej klasie i do nawigacji między przedziałami członków w siatce okna Szczegóły **klasy.**

## <a name="use-the-keyboard-in-class-designer"></a>Używanie klawiatury w Projektancie klas

Następujące akcje klawiatury są obsługiwane na diagramach klas:

|Klucz|Kontekst|Opis|
|---------|-------------|-----------------|
|**Klawisze strzałek**|Kształty typu wewnętrznego|Nawigacja w stylu drzewa na zawartości kształtu (zawijanie wokół kształtu jest obsługiwane). Lewy i prawy klawisz rozwijać/zwijać bieżący element, jeśli jest rozwijalny i przejdź do elementu nadrzędnego, jeśli nie (zobacz nawigację widoku drzewa, aby uzyskać szczegółowe zachowanie).|
|**Klawisze strzałek**|Kształty najwyższego poziomu|Przesuwanie kształtów na diagramie.|
|**Klawisze strzałek shift**+**arrow keys**|Kształty typu wewnętrznego|Tworzenie ciągłego zaznaczania składającego się z elementów kształtu, takich jak elementy członkowskie, typy zagnieżdżone lub przedziały. Te skróty nie obsługują zawijania.|
|**Strona główna**|Kształty typu wewnętrznego|Przejdź do tytułu kształtu najwyższego poziomu.|
|**Strona główna**|Kształty najwyższego poziomu|Przejdź do pierwszego kształtu na diagramie.|
|**Zakończenie**|Kształty typu wewnętrznego|Przejdź do ostatniego widocznego elementu wewnątrz kształtu.|
|**Zakończenie**|Kształty najwyższego poziomu|Przejdź do ostatniego kształtu na diagramie.|
|**Zmiana**+**w domu**|Kształt typu wewnętrznego|Zaznacza elementy w kształcie, zaczynając od bieżącego elementu, a kończąc na najwyższym elemencie o tym samym kształcie.|
|**Koniec zmiany**+**biegów**|Kształt typu wewnętrznego|Tak samo jak **w uchwale Shift**+**Home,** ale w kierunku odgórym.|
|**Wprowadź**|Wszystkie konteksty|Wywołuje domyślną akcję na kształcie, która jest również dostępna za pomocą dwukrotnego kliknięcia. W większości przypadków jest to View Code, ale niektóre elementy definiują go inaczej (lizaki, nagłówki przedziałów, etykiety lizaków).|
|**+** I**-**|Wszystkie konteksty|Jeśli aktualnie skoncentrowany element jest rozwijalny, te klucze rozwinąć lub zwinąć element.|
|**>**|Wszystkie konteksty|Na elementach z elementami podrzędnymi rozszerza element, jeśli jest zwinięty i przechodzi do pierwszego elementu podrzędnego.|
|**<**|Wszystkie konteksty|Przechodzi do elementu nadrzędnego.|
|**Alt**+**Shift**+**L**|Kształty typu ewnętrznego + kształty typu.|Przechodzi do lizaka aktualnie wybranego kształtu, jeśli jest obecny.|
|**Alt**+**Shift**+**B**|Kształty typu ewnętrznego + kształty typu.|Jeśli lista typów podstawowych jest wyświetlana w kształcie typu i zawiera więcej niż jeden element, powoduje to przełączenie stanu rozszerzenia listy (zwiń/rozwiń).|
|**Usuwanie**|W sprawie kształtów tekstu i komentarza|Wywołuje **polecenie Usuń z diagramu.**|
|**Usuwanie**|Na wszystko inne.|Wywołuje **polecenie Usuń z kodu** (elementy członkowskie, parametry, skojarzenia, dziedziczenie, etykiety lizaków).|
|**Usuwanie ctrl**+**Delete**|Wszystkie konteksty|Wywołuje **polecenie Usuń z kodu** przy wyborze.|
|**Zakładka**|Wszystkie konteksty|Przechodzi do następnego dziecka w obrębie tego samego rodzica (obsługuje zawijanie).|
|**Shift**+**Karta** Shift|Wszystkie konteksty|Przechodzi do poprzedniego podrzędnego w obrębie tego samego rodzica (obsługuje zawijanie).|
|**Spacja**|Wszystkie konteksty|Przełącza zaznaczenie w bieżącym elemencie.|

## <a name="use-the-keyboard-in-the-class-details-window"></a>Używanie klawiatury w oknie Szczegóły klasy

> [!NOTE]
> Następujące powiązania klucza zostały wybrane specjalnie do naśladowania doświadczenia pisania kodu.

Użyj następujących klawiszy, aby przejść do okna **Szczegóły klasy:**

|||
|-|-|
|Klucz|Wynik|
|**,** (przecinek)|Jeśli kursor znajduje się w wierszu parametru, wpisanie przecinka powoduje przeniesienie kursora do pola Nazwa następnego parametru. Jeśli kursor znajduje się w ostatnim wierszu parametru metody, przenosi \<kursor do parametru add> pola, którego można użyć do utworzenia nowego parametru.<br /><br /> Jeśli kursor znajduje się w innym miejscu w oknie **Szczegóły klasy,** wpisanie przecinka dosłownie dodaje przecinek w bieżącym polu.|
|**;** (średnik) lub **)** (nawias zamykający)|Przenoszenie kursora do pola Nazwa następnego wiersza elementu członkowskiego w siatce okna **Szczegóły klasy.**|
|**Zakładka**|Przenosi kursor do następnego pola, najpierw przesuwając się od lewej do prawej, a następnie od góry do dołu. Jeśli kursor przechodzi z pola, w którym wpisano tekst, **szczegóły klasy** przetwarza ten tekst i przechowuje go, jeśli nie powoduje wystąpienia błędu.<br /><br /> Jeśli kursor znajduje się na pustym polu, takim jak \<dodawanie parametru>, tabulator przenosi go do pierwszego pola następnego wiersza.|
|**Spacja**|Przenosi kursor do następnego pola, najpierw przesuwając się od lewej do prawej, a następnie od góry do dołu. Jeśli kursor znajduje się na pustym polu, takim jak \<dodawanie parametru>, zostanie przeniesiony do pierwszego pola następnego wiersza. Należy \<zauważyć, że miejsce> wpisane natychmiast po zignorowaniu przecinka.<br /><br /> Jeśli kursor znajduje się w polu Podsumowanie, wpisanie spacji powoduje dodanie znaku spacji.<br /><br /> Jeśli kursor znajduje się w kolumnie Ukryj w danym wierszu, wpisanie spacji powoduje przełączenie wartości pola wyboru Ukryj.|
|**Ctrl**+**Karta** Ctrl|Przełącz się do innego okna dokumentu. Na przykład przełącz się z okna **Szczegóły klasy** do otwartego pliku kodu.|
|**Esc**|Jeśli tekst rozpoczęto w polu, naciśnięcie klawisza ESC działa jako klawisz cofania, przywracając zawartość pola do poprzedniej wartości. Jeśli okno Szczegółów klasy ma ogólny fokus, ale żadna określona komórka nie ma fokusu, naciśnięcie klawisza ESC odsuwa fokus od okna **Szczegóły klasy.**|
|**Strzałka w górę** i **strzałka w dół**|Klawisze te przesuwają kursor z wiersza do wiersza w pionie w siatce okna **Szczegóły klasy.**|
|**Strzałka w lewo**|Jeśli kursor znajduje się w kolumnie Nazwa, naciśnięcie strzałki w lewo powoduje zwijanie bieżącego węzła w hierarchii (jeśli jest ono otwarte).|
|**Strzałka w prawo**|Jeśli kursor znajduje się w kolumnie Nazwa, naciśnięcie strzałki w prawo powoduje rozwinięcie bieżącego węzła w hierarchii (jeśli jest zwinięte).|

## <a name="see-also"></a>Zobacz też

- [Tworzenie i konfigurowanie składowych typów](creating-and-configuring-type-members.md)
- [Jak korzystać z klawiatury wyłącznie](../reference/how-to-use-the-keyboard-exclusively.md)
- [Domyślne skróty klawiaturowe w programie Visual Studio](../default-keyboard-shortcuts-in-visual-studio.md)
- [Skróty klawiaturowe w programie Blend](../../xaml-tools/keyboard-shortcuts-in-blend.md)
