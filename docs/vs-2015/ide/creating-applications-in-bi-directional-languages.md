---
title: Tworzenie aplikacji w językach dwukierunkowych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Hebrew character display, creating applications
- bi-directional language support, about bi-directional language support
- Arabic language, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3b3d8649484178a537ed4af7bdde044a29893275
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619261"
---
# <a name="creating-applications-in-bi-directional-languages"></a>Tworzenie aplikacji w językach dwukierunkowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą programu Visual Studio można tworzyć aplikacje, które prawidłowo wyświetlają tekst w językach pisanych od prawej do lewej, w tym arabski i hebrajski. W przypadku niektórych funkcji można po prostu ustawić właściwości. W innych przypadkach należy zaimplementować funkcje w kodzie.

> [!NOTE]
> Aby móc wprowadzać i wyświetlać języki dwukierunkowe, musisz pracować z wersją systemu Windows, która jest skonfigurowana przy użyciu odpowiedniego języka. Może to być angielska wersja systemu Windows z zainstalowanym odpowiednim pakietem językowym lub odpowiednio zlokalizowaną wersją systemu Windows.

## <a name="types-of-application-that-support-bi-directional-languages"></a>Typy aplikacji, które obsługują Języki dwukierunkowe

1. Aplikacje systemu Windows. Można utworzyć w pełni dwukierunkowe aplikacje, które obejmują obsługę tekstu dwukierunkowego, kolejność odczytywania od prawej do lewej i funkcję dublowania (odwracanie układu okien, menu, okien dialogowych itd.). Z wyjątkiem dublowania te funkcje są dostępne domyślnie lub jako ustawienia właściwości. Dublowanie jest obsługiwane w sposób niezależny dla niektórych funkcji, takich jak okna komunikatów. Jednak w innych przypadkach należy zaimplementować dublowanie w kodzie. Aby uzyskać więcej informacji, zobacz [dwukierunkowa obsługa aplikacji Windows Forms](https://msdn.microsoft.com/library/7b622fa4-f390-4e4d-b624-83a1917cccf2).

2. Aplikacje sieci Web. Usługi sieci Web obsługują i otrzymują wysyłanie tekstu UTF-8 i Unicode, dzięki czemu są odpowiednie dla aplikacji korzystających z języków dwukierunkowych. Aplikacje klienckie sieci Web korzystają z przeglądarek dla ich interfejsów użytkownika, więc stopień dwukierunkowego wsparcia w aplikacji sieci Web zależy od tego, jak dobrze przeglądarka użytkownika obsługuje te funkcje dwukierunkowe. W programie Visual Studio można tworzyć aplikacje obsługujące tekst arabski lub hebrajski, kolejność odczytywania od prawej do lewej, kodowanie plików i ustawienia kultur lokalnych. Aby uzyskać więcej informacji, zobacz [dwukierunkowe wsparcie dla aplikacji sieci Web ASP.NET](https://msdn.microsoft.com/library/5576f9b1-9b86-41ef-8354-092d366bcd03).

3. Aplikacje konsolowe. Aplikacje konsolowe nie obejmują obsługi tekstu w językach dwukierunkowych. Jest to wynikiem działania systemu Windows z aplikacjami konsolowymi.

## <a name="visual-studio-features-that-are-fully-supported"></a>Funkcje programu Visual Studio, które są w pełni obsługiwane
 W czasie projektowania w programie Visual Studio można używać języków dwukierunkowych w następujący sposób:

- **Wprowadzanie tekstu** Program Visual Studio obsługuje kodowanie Unicode, więc jeśli system jest ustawiony na odpowiednie ustawienia regionalne i język wejściowy, możesz wprowadzić tekst w języku arabskim lub hebrajskim. (Obsługa Arabska obejmuje kashida i znaki diakrytyczne).

- **Nazwy obiektów** Za pomocą dwukierunkowych języków można przypisywać nazwy do rozwiązań, projektów, plików, folderów i tak dalej. W kodzie można używać języków dwukierunkowych dla nazw zmiennych, klas, obiektów, atrybutów, metadanych i innych elementów.

- **Kodowanie pliku** Możesz zapisywać i otwierać pliki z kodowaniem specyficznym dla języka lub Unicode. Aby uzyskać więcej informacji, zobacz [jak: zapisywanie i otwieranie plików z kodowaniem](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="features-with-limited-or-no-support"></a>Funkcje z ograniczoną lub bez pomocy technicznej
 Inne funkcje wspólne dla dwukierunkowych aplikacji językowych nie są w pełni obsługiwane w programie Visual Studio lub w niektórych przypadkach, a nie wcale. Należą do nich następujące elementy:

- **Kolejność odczytywania od prawej do lewej** Domyślnie kontrolki wprowadzania tekstu używane w programie Visual Studio używają kolejności czytania od lewej do prawej. W większości przypadków można użyć standardowych gestów systemu Windows, aby przełączyć kolejność odczytywania. Na przykład możesz nacisnąć klawisze Ctrl + Strzałka w prawo, aby przełączyć okno Właściwości do obsługi kolejności odczytywania od prawej do lewej dla wartości właściwości.

  Jednak kolejność odczytywania od prawej do lewej nie jest obsługiwana wszędzie w programie Visual Studio. Wyjątki obejmują:

  - Pola wyboru, listy rozwijane i inne kontrolki w oknach dialogowych programu Visual Studio zawsze używają kolejności odczytywania od lewej do prawej.

  - Edytor kodu (i edytor tekstu) nie obsługuje kolejności odczytywania od prawej do lewej. Możesz wprowadzić tekst w języku dwukierunkowym, ale kolejność odczytywania jest zawsze od lewej do prawej.

## <a name="naming-things-using-arabic-or-hebrew-text"></a>Nazywanie elementów przy użyciu tekstu arabskiego lub hebrajskiego
 Możesz użyć tekstu arabskiego lub hebrajskiego do przypisywania nazw do folderów, zmiennych lub innych obiektów. Podczas pracy z arabskim można użyć dowolnych znaków arabskich, w tym kashida i znaków diakrytycznych.

 Następujące elementy mogą być nazwane przy użyciu języka arabskiego lub hebrajskiego i będą prawidłowo obsługiwane w programie Visual Studio:

- Rozwiązanie, projekt i nazwy plików, w tym wszystkie foldery dołączone do ścieżki projektu. Eksplorator rozwiązań będzie wyświetlać poprawnie nazwy rozwiązań i elementów.

- Zawartość pliku. Możesz otwierać lub zapisywać pliki z kodowaniem Unicode lub z wybraną stroną kodową.

    > [!NOTE]
    > Edytor kodu jest szczególnym przypadkiem. Aby uzyskać szczegółowe informacje, zobacz poniżej.

- Elementy danych. **Eksplorator serwera** będą wyświetlały te elementy poprawnie i umożliwiają ich edycję.

- Elementy skopiowane do Schowka systemu Windows.

- Atrybuty i metadane.

- Wartości właściwości. Możesz użyć tekstu arabskiego lub hebrajskiego w okno Właściwości. Okno pozwala przełączać się między kolejnością czytania od prawej do lewej i od lewej do prawej przy użyciu standardowych naciśnięć klawiszy systemu Windows (CTRL + RightShift dla opcji od prawej do lewej i CTRL + LeftShift w przypadku opcji od lewej do prawej).

- Kod i tekst literału. W edytorze kodu (który jest również edytorem tekstów) można użyć języka arabskiego lub hebrajskiego do nazw klas, funkcji, zmiennych, właściwości, literałów ciągów, atrybutów i tak dalej. Jednak Edytor nie obsługuje kolejności odczytywania od prawej do lewej; tekst zawsze zaczyna się na lewym marginesie.

    > [!TIP]
    > Zaleca się umieszczenie literałów ciągu w plikach zasobów zamiast kodowania ich w programach. Aby uzyskać więcej informacji, zobacz [Przewodnik: lokalizowanie Windows Forms](https://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5).

    > [!NOTE]
    > Musisz być spójny w odniesieniu do obiektów o nazwach w tych językach. Na przykład, jeśli używasz kashida podczas nazywania zmiennej arabskiej, należy zawsze używać kashida w przypadku odwoływania się do tej zmiennej, a wynikiem są błędy.

- Komentarze do kodu. Możesz tworzyć komentarze w języku arabskim lub hebrajskim. Możesz również użyć tych języków w narzędziu Comment Builder.

## <a name="see-also"></a>Zobacz też
 [Dwukierunkowa obsługa aplikacji Windows Forms](https://msdn.microsoft.com/library/7b622fa4-f390-4e4d-b624-83a1917cccf2) obsługa dwukierunkowej [obsługi aplikacji sieci Web](https://msdn.microsoft.com/library/5576f9b1-9b86-41ef-8354-092d366bcd03) , które umożliwiają [globalizację](../ide/globalizing-applications.md) [aplikacji](../ide/localizing-applications.md) ASP.NET aplikacje
