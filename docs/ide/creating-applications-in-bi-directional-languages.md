---
title: Obsługa aplikacji arabski i hebrajski
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Hebrew character display, creating applications
- bi-directional language support, about bi-directional language support
- Arabic language, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4aa75ee12e09d4aa56a112a135a2e9e913b5cd39
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335236"
---
# <a name="create-applications-in-bi-directional-languages"></a>Tworzenie aplikacji w językach dwukierunkowych

Visual Studio umożliwia tworzenie aplikacji, które poprawnie wyświetlania tekstu w językach zapisywane prawej do lewej, łącznie z arabski i hebrajski. W przypadku niektórych funkcji można po prostu ustaw właściwości. W innych przypadkach należy zaimplementować funkcje w kodzie.

> [!NOTE]
> Aby można było wprowadzanie i wyświetlanie językach dwukierunkowych, musisz pracować z wersją systemu Windows, który jest skonfigurowany przy użyciu odpowiedniego języka. Może to być angielska wersja systemu Windows przy użyciu odpowiedniego pakietu języka zainstalowane lub prawidłowo zlokalizowaną wersję Windows.

## <a name="types-of-applications-that-support-bi-directional-languages"></a>Typy aplikacji, które obsługują językach dwukierunkowych

-  Aplikacje Windows

   Możesz tworzyć aplikacje całkowicie dwukierunkowej, umożliwiające obsługę tekstu dwukierunkowego, od prawej do lewej kolejność czytania i dublowanie (cofania układu systemu windows, menu, okna dialogowe i tak dalej). Z wyjątkiem funkcji dublowania, te funkcje są dostępne, domyślnie lub zgodnie z ustawieniami właściwości. Dublowanie obsługę natury niektóre funkcje, takie jak okna komunikatów. Jednak w innych przypadkach należy zaimplementować dublowania w kodzie. Aby uzyskać więcej informacji, zobacz [Dwukierunkowa obsługa aplikacji Windows Forms](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications).

-  Aplikacje internetowe

   Obsługa usług sieci Web, wysyłanie i odbieranie UTF-8 i tekst w formacie Unicode, czemu są odpowiednie dla aplikacji, które obejmują językach dwukierunkowych. Aplikacji klienta sieci Web zależy od przeglądarki dla interfejsu użytkownika, więc stopień Obsługa dwukierunkowych w aplikacji sieci web jest zależny od stopnia przeglądarki użytkownika obsługuje te funkcje dwukierunkowych. W programie Visual Studio możesz tworzyć aplikacje z obsługą tekst arabski lub hebrajski, kolejność czytania od prawej do lewej, kodowanie pliku i ustawienia lokalnych kultury. Aby uzyskać więcej informacji, zobacz [Dwukierunkowa obsługa aplikacji sieci web platformy ASP.NET](https://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03).

Aplikacje konsoli nie uwzględniają tekstu Obsługa języków dwukierunkowych. Jest to wynikiem sposobu działania Windows za pomocą aplikacji konsoli.

## <a name="fully-supported-features"></a>W pełni obsługiwane funkcje

W czasie projektowania w programie Visual Studio można użyć języków dwukierunkowych w następujący sposób:

- **Wprowadzanie tekstu**

   Visual Studio obsługuje Unicode, więc jeśli system jest ustawiony na język i odpowiednie ustawienia regionalne można wprowadzić tekst arabski lub hebrajski. (Obejmuje obsługę języka arabskiego Kashida i znaków diakrytycznych.)

- **Nazwy obiektów**

   Aby przypisać nazwy do rozwiązania, projekty, pliki, foldery i tak dalej, można użyć językach dwukierunkowych. W kodzie używając języków dwukierunkowych nazw zmiennych, klasy, obiektu, atrybuty, metadane i inne elementy.

- **Kodowanie pliku**

   Można zapisywać i otwieranie plików z określonego języka lub kodowanie Unicode. Aby uzyskać więcej informacji, zobacz [jak: Zapisywanie i otwieranie plików z kodowaniem](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="features-with-limited-support"></a>Funkcje z ograniczoną obsługę

### <a name="right-to-left-reading-order"></a>Kolejność czytania od prawej do lewej

Domyślnie kontrolki wprowadzania tekstu w programie Visual Studio używają kolejność czytania od lewej do prawej. W większości przypadków można użyć standardowego gestów Windows Aby przełączać kolejność czytania. Na przykład, możesz nacisnąć przycisk **Ctrl**+**RightShift** przełączyć **właściwości** okna do obsługi kolejność czytania od prawej do lewej dla wartości właściwości. Jednak kolejność czytania od prawej do lewej jest nieobsługiwane wszędzie, gdzie w programie Visual Studio:

- Pola wyboru, listy rozwijane i inne formanty w oknach dialogowych programu Visual Studio należy zawsze używać kolejność czytania od lewej do prawej.

- Edytor kodu (i edytora tekstów) nie obsługuje kolejność czytania od prawej do lewej. Można wprowadzić tekst w języku dwukierunkową kolejność odczytu jest jednak zawsze od lewej do prawej.

## <a name="arabic-or-hebrew-object-names"></a>Nazwy obiektów arabskie i hebrajskie

Tekst arabski lub hebrajski można użyć, aby przypisać nazwy do folderów, zmiennych lub innych obiektów. Jeśli pracujesz w języku arabskim, można użyć znaków arabskich Kashida i znaków diakrytycznych.

Następujące elementy mogą być nazwane, za pomocą arabskie i hebrajskie i są poprawnie obsługiwane w programie Visual Studio:

- Rozwiązanie, projekt i nazwy pliku, w tym wszystkie foldery, które uwzględniasz w ścieżce projektu. **Eksplorator rozwiązań** nazwy rozwiązania i element jest wyświetlany poprawnie.

- Zawartość pliku. Można otworzyć lub zapisywanie plików przy użyciu kodowania Unicode lub ze stroną zaznaczonego kodu.

    > [!NOTE]
    > Edytor kodu obsługuje kolejność czytania od prawej do lewej.

- Elementy danych. **Eksplorator serwera** tych elementów jest wyświetlane prawidłowo i umożliwia ich edytować.

- Skopiowano do Schowka Windows elementy.

- Atrybuty i metadanych.

- Wartości właściwości. Można użyć tekst arabski lub hebrajski w **właściwości** okna. Okno pozwala na przełączanie między kolejność czytania od prawej do lewej i od lewej do prawej, przy użyciu standardowych klawiszy Windows (**Ctrl**+**RightShift** od prawej do lewej i **Ctrl**+**LeftShift** dla od lewej do prawej).

- Kod i tekst dosłowny. W edytorze kodu umożliwia arabskie i hebrajskie nazwę klasy, funkcje, zmienne, właściwości, literałów ciągów, atrybuty i tak dalej. Jednak Edytor obsługuje kolejność czytania od prawej do lewej; tekst zawsze rozpoczyna się na lewym marginesie.

    > [!TIP]
    > Literały ciągów należy umieszczać w plikach zasobów zamiast kodować je w swoich programach. Aby uzyskać więcej informacji, zobacz [zasoby w aplikacjach komputerowych (.NET Framework)](/dotnet/framework/resources/index).

    > [!NOTE]
    > Musi być zgodny w sposób odwoływania się do obiektów o nazwie w arabski i hebrajski. Na przykład jeśli używasz Kashida w nazwach zmienną arabski, należy zawsze używać Kashida przy odwoływaniu się do zmiennej lub błędy spowoduje.

- Komentarze w kodzie. Komentarze można tworzyć w arabski lub hebrajski. Umożliwia także tych języków w narzędziu konstruktora komentarz.