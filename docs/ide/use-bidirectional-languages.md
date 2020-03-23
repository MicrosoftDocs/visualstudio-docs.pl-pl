---
title: Obsługa języka arabskiego i hebrajskiego
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Hebrew character display [Visual Studio]
- bidirectional language support
- Arabic, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57bccfccb77c5a80fd2630680564f88f08d7ca5b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591999"
---
# <a name="support-for-bidirectional-languages-in-visual-studio"></a>Obsługa języków dwukierunkowych w programie Visual Studio

Program Visual Studio może poprawnie wyświetlać tekst arabski i hebrajski oraz umożliwia wprowadzanie tekstu dwukierunkowego dla nazw obiektów i wartości.

> [!NOTE]
> Aby można było wprowadzać i wyświetlać języki dwukierunkowe, należy pracować z wersją systemu Windows skonfigurowaną w odpowiednim języku. Może to być angielska wersja systemu Windows z zainstalowanym odpowiednim pakietem językowym lub odpowiednio zlokalizowana wersja systemu Windows.

## <a name="fully-supported-features"></a>W pełni obsługiwane funkcje

W czasie projektowania w programie Visual Studio można używać języków dwukierunkowych podczas wprowadzania tekstu, nazywania obiektów oraz podczas zapisywania i otwierania plików.

### <a name="text-entry"></a>Wprowadzanie tekstu

Visual Studio obsługuje Unicode, więc jeśli system jest ustawiony na odpowiednie ustawienia regionalne i język wejściowy, można wprowadzić tekst w języku arabskim lub hebrajskim. (Obsługa języka arabskiego obejmuje Kashida i Diakrytyczne).)

### <a name="arabic-or-hebrew-object-names"></a>Nazwy obiektów arabskich lub hebrajskich

Języków dwukierunkowych można używać do przypisywania nazw do rozwiązań, projektów, plików, folderów itd. W kodzie można używać języków dwukierunkowych dla nazw zmiennych, klas, obiektów, atrybutów, metadanych i innych elementów. Podczas pracy z arabskim można używać dowolnych znaków arabskich, w tym Kashida i Diakrytyczne.

Następujące elementy mogą być nazwane przy użyciu arabskiego lub hebrajskiego i są obsługiwane poprawnie przez program Visual Studio:

- Nazwy rozwiązań, projektów i plików, w tym wszystkie foldery uwzględnione w ścieżce projektu.

   **Eksplorator rozwiązań** wyświetla poprawnie nazwy rozwiązań i elementów.

- Zawartość pliku.

   Pliki można otwierać lub zapisywać za pomocą kodowania Unicode lub wybranej strony kodowej.

- Elementy danych.

   **Eksplorator serwera** wyświetla te elementy poprawnie i można je edytować.

- Elementy skopiowane do Schowka systemu Windows.

- Atrybuty i metadane.

- Wartości właściwości.

   W oknie **Właściwości** można użyć tekstu arabskiego lub hebrajskiego. Okno umożliwia przełączanie między kolejnością czytania od prawej do lewej do lewej za pomocą standardowych nacięć klawiszy systemu Windows **(Ctrl**+**RightShift** dla prawej do lewej i **Ctrl**+**LeftShift** dla od lewej do prawej).

- Kod i tekst dosłowny.

   W edytorze kodu można używać języka arabskiego lub hebrajskiego do nazywania klas, funkcji, zmiennych, właściwości, literałów ciągów, atrybutów itd. Jednak edytor nie obsługuje kolejności czytania od prawej do lewej; tekst zawsze zaczyna się na lewym marginesie.

   > [!TIP]
   > Literały ciągów należy umieszczać w plikach zasobów, a nie w programach. Aby uzyskać więcej informacji, zobacz [Zasoby w aplikacjach klasycznych (.NET Framework)](/dotnet/framework/resources/index).

   > [!NOTE]
   > Musisz być spójny w sposobie odwoływania się do obiektów nazwanych w języku arabskim i hebrajskim. Na przykład, jeśli używasz Kashida w nazewnictwie zmiennej arabskiej, należy zawsze używać Kashida podczas odwoływania się do tej zmiennej lub spowoduje to błędy.

- Komentarze do kodu. Komentarze można tworzyć w języku arabskim lub hebrajskim. Można również użyć tych języków w narzędziu konstruktora komentarzy.

### <a name="file-encoding"></a>Kodowanie plików

Pliki można zapisywać i otwierać za pomocą kodowania specyficznego dla języka lub Unicode. Aby uzyskać więcej informacji, zobacz [Jak: Zapisywanie i otwieranie plików z kodowaniem](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="right-to-left-reading-order"></a>Kolejność czytania od prawej do lewej

Visual Studio ma ograniczoną obsługę kolejności odczytu od prawej do lewej. Domyślnie formanty wprowadzania tekstu w programie Visual Studio używają kolejności odczytu od lewej do prawej. W większości przypadków można użyć standardowych gestów systemu Windows, aby przełączyć kolejność odczytu. Na przykład można nacisnąć **klawisz Ctrl**+**RightShift,** aby przełączyć okno **Właściwości,** aby obsługiwać kolejność odczytu od prawej do lewej dla wartości właściwości.

Kolejność odczytu od prawej do lewej nie jest obsługiwana w następujących miejscach w programie Visual Studio:

- Pola wyboru, listy rozwijane i inne formanty w oknach dialogowych programu Visual Studio zawsze używają kolejności odczytu od lewej do prawej.

- Edytor kodu (i edytor tekstu) nie obsługuje kolejności odczytu od prawej do lewej. Tekst można wprowadzać w języku dwukierunkowym, ale kolejność odczytu jest zawsze od lewej do prawej.

## <a name="see-also"></a>Zobacz też

- [Tworzenie zglobalizowanych i zlokalizowanych aplikacji](globalizing-and-localizing-applications.md)
