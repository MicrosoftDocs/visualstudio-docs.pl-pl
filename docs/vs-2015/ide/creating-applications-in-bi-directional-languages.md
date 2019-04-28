---
title: Tworzenie aplikacji w językach dwukierunkowych | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c45f3ac7cfec727eb0a27fc79e5fe09237e8f8c3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437591"
---
# <a name="creating-applications-in-bi-directional-languages"></a>Tworzenie aplikacji w językach dwukierunkowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio umożliwia tworzenie aplikacji, które poprawnie wyświetlania tekstu w językach zapisywane prawej do lewej, łącznie z arabski i hebrajski. W przypadku niektórych funkcji można po prostu ustaw właściwości. W innych przypadkach należy zaimplementować funkcje w kodzie.  
  
> [!NOTE]
> Aby można było wprowadzanie i wyświetlanie językach dwukierunkowych, musisz pracować z wersją systemu Windows, który jest skonfigurowany przy użyciu odpowiedniego języka. Może to być angielska wersja systemu Windows przy użyciu odpowiedniego pakietu języka zainstalowane lub prawidłowo zlokalizowaną wersję Windows.  
  
## <a name="types-of-application-that-support-bi-directional-languages"></a>Typy aplikacji tego Dwukierunkowa obsługa języków  
  
1. Aplikacje Windows. Możesz tworzyć aplikacje całkowicie dwukierunkowej, umożliwiające obsługę tekstu dwukierunkowego, od prawej do lewej kolejność czytania i dublowanie (cofania układu systemu windows, menu, okna dialogowe i tak dalej). Z wyjątkiem funkcji dublowania, te funkcje są dostępne, domyślnie lub zgodnie z ustawieniami właściwości. Dublowanie obsługę natury niektóre funkcje, takie jak okna komunikatów. Jednak w innych przypadkach należy zaimplementować dublowania w kodzie. Aby uzyskać więcej informacji, zobacz [dwukierunkowej obsługę dla Windows Forms aplikacji](http://msdn.microsoft.com/library/7b622fa4-f390-4e4d-b624-83a1917cccf2).  
  
2. Aplikacje sieci Web. Usługi sieci Web pomocy technicznej i odbieranie wysyła tekst UTF-8 i Unicode, czemu są odpowiednie dla aplikacji obejmujące językach dwukierunkowych. Aplikacji klienta sieci Web zależy od przeglądarki dla interfejsu użytkownika, więc stopień Obsługa dwukierunkowych w aplikacji sieci Web jest zależny od stopnia przeglądarki użytkownika obsługuje te funkcje dwukierunkowych. W programie Visual Studio możesz tworzyć aplikacje z obsługą tekst arabski lub hebrajski, kolejność czytania od prawej do lewej, kodowanie pliku i ustawienia lokalnych kultury. Aby uzyskać więcej informacji, zobacz [Dwukierunkowa obsługa aplikacji sieci Web platformy ASP.NET](http://msdn.microsoft.com/library/5576f9b1-9b86-41ef-8354-092d366bcd03).  
  
3. Aplikacje konsoli. Aplikacje konsoli nie uwzględniają tekstu Obsługa języków dwukierunkowych. Jest to wynikiem sposobu działania Windows za pomocą aplikacji konsoli.  
  
## <a name="visual-studio-features-that-are-fully-supported"></a>Funkcje programu Visual Studio, które są w pełni obsługiwane  
 W czasie projektowania w programie Visual Studio można użyć języków dwukierunkowych w następujący sposób:  
  
- **Wprowadzanie tekstu** programu Visual Studio obsługuje Unicode, więc jeśli system jest ustawiony na język i odpowiednie ustawienia regionalne można wprowadzić tekst arabski lub hebrajski. (Obejmuje obsługę języka arabskiego Kashida i znaków diakrytycznych.)  
  
- **Nazwy obiektów** językach dwukierunkowych można użyć, aby przypisać nazwy do rozwiązania, projekty, pliki, foldery i tak dalej. W kodzie używając języków dwukierunkowych nazw zmiennych, klasy, obiektu, atrybuty, metadane i inne elementy.  
  
- **Kodowanie pliku** można zapisać i otwieranie plików z określonego języka lub kodowanie Unicode. Aby uzyskać więcej informacji, zobacz [jak: Zapisywanie i otwieranie plików z kodowaniem](../ide/how-to-save-and-open-files-with-encoding.md).  
  
## <a name="features-with-limited-or-no-support"></a>Funkcje z ograniczonym lub brak obsługi  
 Inne funkcje, które są wspólne dla języków dwukierunkowych aplikacje nie są w pełni obsługiwane w programie Visual Studio lub w niektórych przypadkach, w ogóle nie. Należą do nich następujące elementy:  
  
- **Kolejność czytania od prawej do lewej** kontrolki wprowadzania tekstu, użyj w programie Visual Studio używają domyślnie kolejność czytania od lewej do prawej. W większości przypadków można użyć standardowego gestów Windows Aby przełączać kolejność czytania. Na przykład można nacisnąć klawisz Shift Ctrl + Strzałka w prawo, aby przełączyć okno właściwości aby obsługiwać kolejność czytania od prawej do lewej dla wartości właściwości.  
  
     Jednak kolejność czytania od prawej do lewej jest nieobsługiwane wszędzie, gdzie w programie Visual Studio. Wyjątki obejmują:  
  
    - Pola wyboru, listy rozwijane i inne formanty w oknach dialogowych programu Visual Studio należy zawsze używać kolejność czytania od lewej do prawej.  
  
    - Edytor kodu (i edytora tekstów) nie obsługuje kolejność czytania od prawej do lewej. Można wprowadzić tekst w języku dwukierunkową kolejność odczytu jest jednak zawsze od lewej do prawej.  
  
## <a name="naming-things-using-arabic-or-hebrew-text"></a>Nazewnictwo rzeczy przy użyciu arabski lub hebrajski tekstu  
 Tekst arabski lub hebrajski można użyć, aby przypisać nazwy do folderów, zmiennych lub innych obiektów. Jeśli pracujesz w języku arabskim, można użyć znaków arabskich Kashida i znaków diakrytycznych.  
  
 Następujące elementy mogą być nazwane, za pomocą arabskie i hebrajskie i będzie obsługiwany poprawnie w programie Visual Studio:  
  
- Rozwiązanie, projekt i nazwy pliku, w tym wszystkie foldery, które uwzględniasz w ścieżce projektu. Eksplorator rozwiązań będą wyświetlane nazwy rozwiązania i element poprawnie.  
  
- Zawartość pliku. Można otworzyć lub zapisywanie plików przy użyciu kodowania Unicode lub ze stroną zaznaczonego kodu.  
  
    > [!NOTE]
    > Edytor kodu jest przypadkiem szczególnym. Aby uzyskać szczegółowe informacje Zobacz poniżej.  
  
- Elementy danych. **Eksplorator serwera** będzie poprawnie wyświetlić tych elementów i pozwalają je edytować.  
  
- Skopiowano do Schowka Windows elementy.  
  
- Atrybuty i metadanych.  
  
- Wartości właściwości. W oknie dialogowym właściwości, można użyć tekst arabski lub hebrajski. Okno pozwala przełączać się między kolejność czytania od prawej do lewej i od lewej do prawej, przy użyciu standardowych klawiszy Windows (CTRL + RightShift dla od prawej do lewej i CTRL + LeftShift dla od lewej do prawej).  
  
- Kod i tekst dosłowny. W edytorze kodu (jest to również edytora tekstów) umożliwia arabskie i hebrajskie nazwę klasy, funkcje, zmienne, właściwości, literałów ciągów, atrybuty i tak dalej. Jednak Edytor obsługuje kolejność czytania od prawej do lewej; tekst zawsze rozpoczyna się na lewym marginesie.  
  
    > [!TIP]
    > Zaleca się umieścić literałów ciągów w plikach zasobów zamiast kodować je w swoich programach. Aby uzyskać więcej informacji, zobacz [instruktażu: Lokalizowanie formularzy Windows](http://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5).  
  
    > [!NOTE]
    > Użytkownik musi być zgodne, w jaki sposób odwoływania się do obiektów o nazwie w tych językach. Na przykład jeśli używasz Kashida w nazwach zmienną arabski, należy zawsze używać Kashida przy odwoływaniu się do tej zmiennej lub będą powodować błędy.  
  
- Komentarze w kodzie. Komentarze można tworzyć w arabski lub hebrajski. Umożliwia także tych języków w narzędziu konstruktora komentarz.  
  
## <a name="see-also"></a>Zobacz też  
 [Dwukierunkowa obsługa Windows Forms aplikacji](http://msdn.microsoft.com/library/7b622fa4-f390-4e4d-b624-83a1917cccf2)   
 [Dwukierunkowa obsługa aplikacji sieci Web ASP.NET](http://msdn.microsoft.com/library/5576f9b1-9b86-41ef-8354-092d366bcd03)   
 [Globalizowanie aplikacji](../ide/globalizing-applications.md)   
 [Lokalizowanie aplikacji](../ide/localizing-applications.md)
