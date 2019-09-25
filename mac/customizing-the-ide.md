---
title: Dostosowywanie środowiska IDE
description: Visual Studio dla komputerów Mac można dostosować na różne sposoby, umożliwiając użytkownikom opracowywanie aplikacji w środowisku, które spełniają zarówno ich wydajność, jak i estetyczne potrzeby. W tym artykule przedstawiono różne sposoby dostosowania Visual Studio dla komputerów Mac do własnych potrzeb.
author: alanjclark
ms.author: alcl
ms.date: 05/06/2018
ms.assetid: F7C2A28C-0759-4E0D-A28E-B72D5AB73DB6
ms.custom: video
ms.openlocfilehash: fa1e2924e810f9e37f28d5becdfd8d46243b76fe
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71213743"
---
# <a name="customizing-the-ide"></a>Dostosowywanie środowiska IDE

Visual Studio dla komputerów Mac można dostosować, umożliwiając użytkownikom opracowywanie aplikacji w środowisku, które zaspokaja ich potrzeby w zakresie wydajności i estetyczności. W tym artykule przedstawiono różne sposoby dostosowania Visual Studio dla komputerów Mac do własnych potrzeb.

## <a name="dark-theme"></a>Motyw ciemny

![Ciemny widok motywu](media/customizing-the-ide-image7a.png)

Możesz przełączyć motywy w Visual Studio dla komputerów Mac, przechodząc do okna **preferencji > programu Visual Studio > środowisko > stylu wizualizacji** i wybierając żądany motyw z listy rozwijanej **motyw interfejsu użytkownika** , jak pokazano na poniższej ilustracji:

![Ciemny wybór motywu](media/customizing-the-ide-image7b.png)

## <a name="localization"></a>Lokalizacja

Visual Studio dla komputerów Mac jest lokalizowana w następujących 14 językach, dzięki czemu można uzyskać dostęp do większej liczby deweloperów:

* Chiński — Chiny
* Chiński — Tajwan
* czeski
* Francuski
* niemiecki
* Angielski
* Włoski
* Japoński
* koreański
* polski
* Portugalski (Brazylia)
* Rosyjski
* Hiszpański
* turecki

Aby zmienić język wyświetlany przez Visual Studio dla komputerów Mac, przejdź do **okna preferencji > programu Visual Studio > środowisku > stylu wizualizacji** i wybierz żądany język z listy rozwijanej **język interfejsu użytkownika** , jak pokazano w poniższej tabeli. Image

![Wybór języka](media/customizing-the-ide-image11a.png)

## <a name="author-information"></a>Informacje o autorze

Panel Informacje o autorze umożliwia dodanie odpowiednich informacji o sobie, takich jak imię i nazwisko, adres e-mail, właściciel praw autorskich dla swojej pracy, firmy i znaku towarowego:

![Edytuj sekcję informacji o autorze](media/customizing-the-ide-image9a.png)

Te informacje służą do wypełniania standardowych nagłówków plików, takich jak licencja, które mogą zostać dodane do nowych plików:

![Opcje nagłówka standardowego](media/customizing-the-ide-image8a.png)

Wypełnione **nazwy** i pola **poczty e-mail** będą używane w każdym zatwierdzeniu, które odbywa się za pośrednictwem kontroli wersji w Visual Studio dla komputerów Mac. Jeśli te pola nie zostały wypełnione, Visual Studio dla komputerów Mac wyświetli monit o to, gdy spróbujesz użyć kontroli wersji.

## <a name="key-bindings"></a>Powiązania kluczy

Kluczowe powiązania lub skróty klawiaturowe umożliwiają dostosowanie środowiska programistycznego, co pozwala na efektywniejsze przechodzenie w Visual Studio dla komputerów Mac. Zapewnia znane kluczowe powiązania dla wielu popularnych środowisk IDE, takich jak Visual Studio (w systemie Windows), programy do powiększania, Visual Studio Code i Xcode.

Powiązania kluczy można ustawić przez przechodzenie do **preferencji > programu Visual Studio > > kluczowe powiązania środowiska**, jak pokazano na poniższej ilustracji:

![Ustawianie powiązań kluczy](media/customizing-the-ide-image10a.png)

W tym miejscu możesz wyszukiwać kombinacje kluczy powiązań, wyświetlać powiązania powodujące konflikty, dodawać nowe powiązania i edytować istniejące powiązania.

Te powiązania można również ustawić podczas początkowej konfiguracji Visual Studio dla komputerów Mac przy użyciu ekranu **wyboru klawiatury** :

![Ustawianie powiązań kluczy, pierwsze uruchomienie](media/ide-tour-2019-keyboard-shortcut.png)

## <a name="workspace-layout"></a>Układ obszaru roboczego

Obszar roboczy Visual Studio dla komputerów Mac składa się z głównego obszaru dokumentu (zwykle edytora, powierzchni projektanta lub pliku opcji), otoczone przez uzupełniające *konsole* zawierające przydatne informacje umożliwiające dostęp do plików aplikacji, testowanie i debugera.

 ![Układ obszaru roboczego](media/customizing-the-ide-image1a.png)

### <a name="viewing-and-arranging-pads"></a>Przeglądanie i rozmieszczanie konsol

Po otwarciu nowego rozwiązania lub pliku w Visual Studio dla komputerów Mac należy zauważyć, że niektóre *konsole* znajdują się w obszarze roboczym, w tym okienko rozwiązania, konspekt dokumentu i błędy:

![Konsole rozwiązań](media/customizing-the-ide-image2a.png)

Visual Studio dla komputerów Mac zawiera konsole zawierające dodatkowe informacje, narzędzia i ułatwienia nawigacji, do których wszystkie są dostępne, przechodząc do **widoku widok > konsole** , a następnie wybierając konsolę, aby ją dodać:

![Wybierz nową konsolę](media/customizing-the-ide-image3a.png)

Konsole mogą być również otwierane automatycznie przez różne polecenia, takie jak **Znajdź w plikach** (Shift + Cmd + F), które otwiera odłączoną konsolę wyników wyszukiwania.

Konsole można przenosić i rozmieszczać w całym przepływie pracy w dowolny sposób, który jest najbardziej przydatny dla Ciebie. Na przykład można zadokować je na dowolnej stronie edytora dokumentów, sąsiadująco z inną konsolą, powyżej lub pod inną konsolą lub jako zestaw konsol z kartami, dzięki czemu można szybko przełączać się między nimi.

W przypadku często używanych konsol można również całkowicie odłączyć konsolę od okna Visual Studio dla komputerów Mac i utworzyć osobne okno dla tej konsoli.

Konsole mogą być ukrywane i zamykane za pomocą przełączników w prawym górnym rogu poszczególnych konsol:

![Ukrywanie i zamykanie konsol](media/customizing-the-ide-image5a.png)

Autoukryte konsole są zadokowane po bokach obszaru roboczego, dzięki czemu są one łatwo dostępne, gdy są wymagane. Umieszczenie kursora nad konsolą zostanie ponownie wyświetlone i zostanie ono ukryte, gdy wskaźnik myszy i fokusu zostanie pozostawiony.

### <a name="organizing-layouts"></a>Organizowanie układów

Konsole, które są wyświetlane w dowolnym momencie, są zależne od bieżącego kontekstu. Na przykład podczas korzystania z projektanta wizualnego, Przybornik i konsole siatki właściwości są najważniejsze. podczas debugowania przydatne jest posiadanie konsol debugera do wyświetlania stosu i elementów lokalnych.

Stan otwartych multiplekserów jest reprezentowany przez *Układ*. Układy można przełączać ręcznie za pomocą menu Widok, jak pokazano na poniższej ilustracji, lub są automatycznie przełączane podczas wykonywania akcji, takich jak debugowanie lub otwieranie scenorysu:

![Wybieranie nowych układów](media/customizing-the-ide-image6b.png)

Zawsze istnieje aktywny układ i wszelkie zmiany wprowadzone w układzie, takie jak dodanie lub zmiana położenia konsoli, spowoduje jedynie zmianę aktywnego układu. Po zamknięciu Visual Studio dla komputerów Mac wprowadzone zmiany nie zostaną zapisane.

Istnieje jednak możliwość utworzenia nowego układu przy użyciu elementu menu **widok > Zapisz bieżący układ** . To polecenie spowoduje dodanie bieżącego układu do menu, aby można było je wybrać w dowolnym momencie:

![Zapisz bieżący układ](media/customizing-the-ide-image6a.png)

### <a name="side-by-side-editing-support"></a>Obsługa edycji równoczesnej

Visual Studio dla komputerów Mac pozwala na otwieranie edytorów tekstu obok siebie lub w celu uzyskania edytora jako odłączonego okna.

Tryb dwóch kolumn można włączyć za pomocą elementu menu Widok, wybierając opcję **wyświetl > kolumny edytora > 2 kolumny**lub przeciągając kartę edytora do jednej z krawędzi obszaru edytora:

![Dwukolumnowy tryb Side-by-Side](media/customizing-the-ide-sbs.png)

Tabulatory edytora można przeciągać poza obszar dokumentu w celu utworzenia przepływającego okna edytora. To przestawne okno obsługuje również edytorów równoległych i może zawierać kilka kart edytora:

![Utwórz nowe okno](media/customizing-the-ide-sbs1.png)

![Dwie kolumny obok siebie z dodatkowymi kartami](media/customizing-the-ide-sbs2.png)

Aby przywrócić pojedynczy otwarty Edytor, wybierz pozycję **wyświetl > kolumny edytora > 1 kolumna**.

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Customize-the-Look-and-Feel/player]

## <a name="see-also"></a>Zobacz także

- [Personalizowanie środowiska IDE programu Visual Studio (w systemie Windows)](/visualstudio/ide/personalizing-the-visual-studio-ide)