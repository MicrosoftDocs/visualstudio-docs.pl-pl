---
title: Obsługa arabski i hebrajski
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Hebrew character display [Visual Studio]
- bidirectional language support
- Arabic, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1271e5160920dc79decc9acc98aa1e5e3d936ca5
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66823562"
---
# <a name="support-for-bidirectional-languages-in-visual-studio"></a>Obsługa języków dwukierunkowych w programie Visual Studio

Visual Studio poprawnie wyświetlić tekst arabski i hebrajski i umożliwia wprowadzenie tekstu dwukierunkowego dla nazwy obiektów i wartości.

> [!NOTE]
> Aby można było wprowadzanie i wyświetlanie języki dwukierunkowe, musisz pracować z wersją systemu Windows, który jest skonfigurowany przy użyciu odpowiedniego języka. Może to być angielska wersja systemu Windows przy użyciu odpowiedniego pakietu języka zainstalowane lub prawidłowo zlokalizowaną wersję Windows.

## <a name="fully-supported-features"></a>W pełni obsługiwane funkcje

W czasie projektowania w programie Visual Studio używając języków dwukierunkowych podczas wprowadzania tekstu, nazewnictwa obiektów, a podczas zapisywania i otwierania plików.

### <a name="text-entry"></a>Wprowadzanie tekstu

Visual Studio obsługuje Unicode, więc jeśli system jest ustawiony na język i odpowiednie ustawienia regionalne można wprowadzić tekst arabski lub hebrajski. (Obejmuje obsługę języka arabskiego Kashida i znaków diakrytycznych.)

### <a name="arabic-or-hebrew-object-names"></a>Nazwy obiektów arabskie i hebrajskie

Języki dwukierunkowe można użyć, aby przypisać nazwy do rozwiązania, projekty, pliki, foldery i tak dalej. W kodzie można użyć języki dwukierunkowe nazw zmiennych, klasy, obiektu, atrybuty, metadane i inne elementy. Jeśli pracujesz w języku arabskim, można użyć znaków arabskich Kashida i znaków diakrytycznych.

Następujące elementy mogą być nazwane, za pomocą arabskie i hebrajskie i są poprawnie obsługiwane przez program Visual Studio:

- Rozwiązanie, projekt i nazwy pliku, w tym wszystkie foldery, które uwzględniasz w ścieżce projektu.

   **Eksplorator rozwiązań** nazwy rozwiązania i element jest wyświetlany poprawnie.

- Zawartość pliku.

   Można otworzyć lub zapisywanie plików przy użyciu kodowania Unicode lub ze stroną zaznaczonego kodu.

- Elementy danych.

   **Eksplorator serwera** tych elementów jest wyświetlane prawidłowo i można je edytować.

- Skopiowano do Schowka Windows elementy.

- Atrybuty i metadanych.

- Wartości właściwości.

   Można użyć tekst arabski lub hebrajski w **właściwości** okna. Okno pozwala na przełączanie między kolejność czytania od prawej do lewej i od lewej do prawej, przy użyciu standardowych klawiszy Windows (**Ctrl**+**RightShift** od prawej do lewej i **Ctrl**+**LeftShift** dla od lewej do prawej).

- Kod i tekst dosłowny.

   W edytorze kodu umożliwia arabskie i hebrajskie nazwę klasy, funkcje, zmienne, właściwości, literałów ciągów, atrybuty i tak dalej. Jednak Edytor obsługuje kolejność czytania od prawej do lewej; tekst zawsze rozpoczyna się na lewym marginesie.

   > [!TIP]
   > Literały ciągów należy umieszczać w plikach zasobów zamiast kodować je w swoich programach. Aby uzyskać więcej informacji, zobacz [zasoby w aplikacjach komputerowych (.NET Framework)](/dotnet/framework/resources/index).

   > [!NOTE]
   > Musi być zgodny w sposób odwoływania się do obiektów o nazwie w arabski i hebrajski. Na przykład jeśli używasz Kashida w nazwach zmienną arabski, należy zawsze używać Kashida przy odwoływaniu się do zmiennej lub błędy spowoduje.

- Komentarze w kodzie. Komentarze można tworzyć w arabski lub hebrajski. Umożliwia także tych języków w narzędziu konstruktora komentarz.

### <a name="file-encoding"></a>Kodowanie pliku

Można zapisywać i otwieranie plików z określonego języka lub kodowanie Unicode. Aby uzyskać więcej informacji, zobacz [jak: Zapisywanie i otwieranie plików z kodowaniem](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="right-to-left-reading-order"></a>Kolejność czytania od prawej do lewej

Program Visual Studio ma ograniczoną obsługę kolejność czytania od prawej do lewej. Domyślnie kontrolki wprowadzania tekstu w programie Visual Studio używają kolejność czytania od lewej do prawej. W większości przypadków można użyć standardowego gestów Windows Aby przełączać kolejność czytania. Na przykład, możesz nacisnąć przycisk **Ctrl**+**RightShift** przełączyć **właściwości** okna do obsługi kolejność czytania od prawej do lewej dla wartości właściwości.

Kolejność czytania od prawej do lewej nie jest obsługiwana w następujących miejscach w programie Visual Studio:

- Pola wyboru, listy rozwijane i inne formanty w oknach dialogowych programu Visual Studio należy zawsze używać kolejność czytania od lewej do prawej.

- Edytor kodu (i edytora tekstów) nie obsługuje kolejność czytania od prawej do lewej. Można wprowadzić tekst w języku dwukierunkową kolejność odczytu jest jednak zawsze od lewej do prawej.

## <a name="see-also"></a>Zobacz także

- [Tworzenie aplikacji uniwersalnych i zlokalizowanych](globalizing-and-localizing-applications.md)
