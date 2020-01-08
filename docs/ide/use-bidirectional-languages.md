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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591999"
---
# <a name="support-for-bidirectional-languages-in-visual-studio"></a>Obsługa języków dwukierunkowych w programie Visual Studio

Program Visual Studio może poprawnie wyświetlać tekst arabski i hebrajski oraz umożliwia wprowadzanie tekstu dwukierunkowego dla nazw obiektów i wartości.

> [!NOTE]
> Aby móc wprowadzać i wyświetlać języki dwukierunkowe, musisz pracować z wersją systemu Windows, która jest skonfigurowana przy użyciu odpowiedniego języka. Może to być angielska wersja systemu Windows z zainstalowanym odpowiednim pakietem językowym lub odpowiednio zlokalizowaną wersją systemu Windows.

## <a name="fully-supported-features"></a>W pełni obsługiwane funkcje

W czasie projektowania w programie Visual Studio można używać języków dwukierunkowych podczas wprowadzania tekstu, nazywania obiektów i podczas zapisywania i otwierania plików.

### <a name="text-entry"></a>Wprowadzanie tekstu

Program Visual Studio obsługuje kodowanie Unicode, więc jeśli system jest ustawiony na odpowiednie ustawienia regionalne i język wejściowy, możesz wprowadzić tekst w języku arabskim lub hebrajskim. (Obsługa Arabska obejmuje kashida i znaki diakrytyczne).

### <a name="arabic-or-hebrew-object-names"></a>Nazwy obiektów arabskiej lub hebrajskich

Można używać języków dwukierunkowych do przypisywania nazw do rozwiązań, projektów, plików, folderów i tak dalej. W kodzie można używać języków dwukierunkowych dla nazw zmiennych, klas, obiektów, atrybutów, metadanych i innych elementów. Podczas pracy z arabskim można użyć dowolnych znaków arabskich, w tym kashida i znaków diakrytycznych.

Następujące elementy mogą być nazwane przy użyciu języka arabskiego lub hebrajskiego i są obsługiwane poprawnie przez program Visual Studio:

- Rozwiązanie, projekt i nazwy plików, w tym wszystkie foldery dołączone do ścieżki projektu.

   **Eksplorator rozwiązań** prawidłowo wyświetla nazwy rozwiązań i elementów.

- Zawartość pliku.

   Możesz otwierać lub zapisywać pliki z kodowaniem Unicode lub z wybraną stroną kodową.

- Elementy danych.

   **Eksplorator serwera** prawidłowo wyświetla te elementy i można je edytować.

- Elementy skopiowane do Schowka systemu Windows.

- Atrybuty i metadane.

- Wartości właściwości.

   Możesz użyć tekstu arabskiego lub hebrajskiego w oknie **Właściwości** . Okno pozwala przełączać się między kolejnością czytania od prawej do lewej i od lewej do prawej przy użyciu standardowych naciśnięć klawiszy systemu Windows (**Ctrl**+**RightShift** dla kierunku od prawej do lewej i **Ctrl**+**LeftShift** w przypadku opcji od lewej do prawej).

- Kod i tekst literału.

   W edytorze kodu można użyć języka arabskiego lub hebrajskiego do nazw klas, funkcji, zmiennych, właściwości, literałów ciągów, atrybutów i tak dalej. Jednak Edytor nie obsługuje kolejności odczytywania od prawej do lewej; tekst zawsze zaczyna się na lewym marginesie.

   > [!TIP]
   > W plikach zasobów należy umieścić literały ciągu, a nie twarde kodowanie ich w programach. Aby uzyskać więcej informacji, zobacz [zasoby w aplikacjach klasycznych (.NET Framework)](/dotnet/framework/resources/index).

   > [!NOTE]
   > Musisz być spójny w odniesieniu do obiektów o nazwach w języku arabskim i hebrajskim. Na przykład jeśli używasz kashida podczas nazywania zmiennej arabskiej, należy zawsze używać kashida w przypadku odwoływania się do tej zmiennej lub błędów.

- Komentarze do kodu. Możesz tworzyć komentarze w języku arabskim lub hebrajskim. Możesz również użyć tych języków w narzędziu Comment Builder.

### <a name="file-encoding"></a>Kodowanie pliku

Możesz zapisywać i otwierać pliki z kodowaniem specyficznym dla języka lub Unicode. Aby uzyskać więcej informacji, zobacz [jak: zapisywanie i otwieranie plików z kodowaniem](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="right-to-left-reading-order"></a>Kolejność odczytywania od prawej do lewej

Program Visual Studio ma ograniczoną obsługę kolejności odczytywania od prawej do lewej. Domyślnie formanty wprowadzania tekstu w programie Visual Studio używają kolejności czytania od lewej do prawej. W większości przypadków można użyć standardowych gestów systemu Windows, aby przełączyć kolejność odczytywania. Na przykład możesz nacisnąć klawisz **Ctrl**+**RightShift** , aby przełączyć okno **Właściwości** do obsługi kolejności odczytywania od prawej do lewej dla wartości właściwości.

Kolejność odczytywania od prawej do lewej nie jest obsługiwana w następujących miejscach w programie Visual Studio:

- Pola wyboru, listy rozwijane i inne kontrolki w oknach dialogowych programu Visual Studio zawsze używają kolejności odczytywania od lewej do prawej.

- Edytor kodu (i edytor tekstu) nie obsługuje kolejności odczytywania od prawej do lewej. Możesz wprowadzić tekst w języku dwukierunkowym, ale kolejność odczytywania jest zawsze od lewej do prawej.

## <a name="see-also"></a>Zobacz także

- [Opracowywanie aplikacji globalnych i zlokalizowanych](globalizing-and-localizing-applications.md)
