---
title: Organizowanie obiektów w kontenery układów w Projektancie XAML | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3ca6fc205585d832f4dadc5f4ce4709a71c7b6fe
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059204"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>Organizowanie obiektów w kontenery układów w projektancie XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wyobraź sobie, gdzie ma się obiekty na stronie; obiekty, takie jak obrazy, przyciski i filmy wideo. Być może ma pojawiać się w wiersze i kolumny, w jednym wierszu w pionie lub w poziomie lub w stałym położeniu.  
  
 Po został mieli Państwo możliwość zastanów się wygląd strony, wybierz panel układu. Wszystkie strony uruchomić przy użyciu jednego, ponieważ potrzebujesz czegoś, aby dodać obiekty do. Domyślnie jest **siatki** , ale można ją zamienić.  
  
 Panele układów ułatwiają rozmieścić obiekty na stronie, ale ich nie więcej niż. One ułatwiają projektowanie dla różnych rozmiarów ekranu i rozwiązania. Jeśli użytkownicy uruchamiają aplikację, wszystko w panelu układu zmienia rozmiar do dopasowania powierzchnię ekranu urządzenia z systemem. Oczywiście jeśli nie chcesz układu w taki sposób, aby to zrobić, można zastąpić to zachowanie dla części układu lub całego układu. Właściwości height i width służy do kontrolowania, który.  
  
 Ta strona opisuje panele układów i kontrolek, a następnie kieruje krótkie filmy wideo, które ułatwiają Rozpoczynanie pracy z nimi.  
  
> [!NOTE]
>  Niektóre filmy wideo mogą odwoływać się do mieszania lub Expression Blend, która za pomocą tego samego projektanta XAML programu Visual Studio i Blend for Visual Studio.  
  
## <a name="layout-panels"></a>Panele układów  
 Twoja strona początkowa, wybierając jedną z tych paneli układu. Strona może mieć więcej niż jeden. Na przykład możesz zacząć od **siatki** Układ panelu, a następnie dodaj **StackPanel** do obszaru w **siatki** , dzięki czemu można rozmieścić formanty w pionie w tym elemencie.  
  
 Poniższe panele układów to najbardziej co jest często używane, ale istnieją inne osoby. Można je znaleźć w **zasoby** panelu.  
  
- [Siatka](#Grid)  
  
- [UniformGrid](#Uniform)  
  
- [Kanwa](#Canvas)  
  
- [StackPanel](#Stack)  
  
- [WrapPanel](#Wrap)  
  
- [DockPanel](#Dock)  
  
### <a name="Grid"></a> Siatka  
 Rozmieść obiekty w wiersze i kolumny.  
  
 ![](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png "98b234b2-ac3b-441f-9136-98375fee87b7")  
  
 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [przy użyciu siatki](http://www.popscreen.com/v/6A4hj/Microsoft-Expression-Blend-Using-Grids)  
  
### <a name="Uniform"></a> UniformGrid  
 Rozmieść obiekty w regionach równym lub jednolite, siatki. Ten panel to idealne narzędzie do porządkowanie listy obrazów.  
  
 ![](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png "928b9284-a7e8-4678-875a-656b80b78076")  
  
 (Dostępne tylko dla projektów WPF)  
  
 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Praca z UniformGrid](http://www.popscreen.com/v/6A4iq/Microsoft-Expression-Blend-Working-with-a-UniformGrid)  
  
### <a name="Canvas"></a> Kanwy  
 Rozmieść obiekty w jakikolwiek sposób, który ma. Jeśli użytkownicy uruchamiają aplikację, te elementy zostaną stałe pozycje, na ekranie.  
  
 ![](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png "e1ae27f0-3a57-454e-b580-877dcea8836d")  
  
 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Praca z obszaru roboczego](http://www.popscreen.com/v/6A4hT/Microsoft-Expression-Blend-Working-with-the-Canvas)  
  
### <a name="Stack"></a> StackPanel  
 Rozmieść obiekty w jednym wierszu, poziomo czy pionowo.  
  
 ![](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png "a85a7b57-b0a8-495e-b985-f0291e41d093")  
  
 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Praca z StackPanel i WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
### <a name="Wrap"></a> WrapPanel  
 Rozmieść obiekty sekwencyjnie od lewej do prawej. Gdy zespół zabraknie miejsca przy prawej krawędzi, jego *opakowuje* zawartość do następnego wiersza, i tak dalej od lewej do prawej, od góry do dołu. Można również ustawić orientacja zawijanego panelu pionie, tak aby obiekty przepływu od góry do dołu i od lewej do prawej.  
  
 (Dostępne tylko dla projektów WPF)  
  
 ![](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png "b1c415fb-9a32-4a18-aa0b-308fca994ac9")  
  
 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Praca z StackPanel i WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
### <a name="Dock"></a> DockPanel  
 Rozmieszczanie obiektów, więc, że pozostają, lub *zadokować*, jednej krawędzi panelu.  
  
 (Dostępne tylko dla projektów WPF)  
  
 ![](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png "72d46b58-9a49-4dd5-8af7-6843c0440226")  
  
 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [WPF — DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)  
  
## <a name="layout-controls"></a>Formanty układu  
 Możesz dodać obiekty do układu kontrolek także. Nie są one jako wiele funkcji, jak panel układu, ale mogą je znaleźć przydatne w niektórych scenariuszach.  
  
 Najbardziej co jest często używane są następujące elementy sterujące układ, ale istnieją inne osoby. Można je znaleźć w **zasoby** panelu.  
  
- [Obramowanie](#Border)  
  
- [Popup](#Popup)  
  
- [ScrollViewer](#Scroll)  
  
- [UniformGrid](#Uniform)  
  
- [Okno widoku](#View)  
  
### <a name="Border"></a> Obramowanie  
 Utwórz obramowanie i/lub tło wokół obiektu. Można dodawać tylko jednego obiektu do **obramowania**. Jeśli chcesz zastosować krawędzi i tła dla więcej niż jednego obiektu, Dodaj panelu układu, aby **obramowania**. Następnie należy dodać obiekty do tego panel lub kontrolka.  
  
 ![](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png "e761238b-99fd-43c5-bbc4-57538b8289ff")  
  
 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Praca z obramowania](http://www.popscreen.com/v/6A4hB/Microsoft-Expression-Blend-Working-with-Borders)  
  
### <a name="Popup"></a> Okno podręczne  
 Pokaż informacje lub użytkownikom w oknie opcji. Można dodawać tylko jednego obiektu do **okno podręczne**. Domyślnie **okno podręczne** zawiera **siatki** , ale można ją zamienić.  
  
### <a name="Scroll"></a> ScrollViewer  
 Włącz używa do przewiń w dół strony lub części strony. Można dodawać tylko jednego obiektu do **ScrollViewer** dzięki temu jest bardzo rozsądne, aby dodać panel układu, takich jak **siatki** lub **StackPanel**.  
  
 ![](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png "06b326d4-f23d-41a6-b26b-e1aff37572a7")  
  
### <a name="View"></a> Okna widoku  
 Skalowanie obiektów, podobnie jak w przypadku Kontrolka powiększenia. Można dodawać tylko jednego obiektu do **Viewbox**. Jeśli chcesz zastosować ten efekt do więcej niż jednego obiektu, Dodaj panelu układu, aby **ViewBox**, a następnie dodać kontrolki do panelu układów.  
  
 (Dostępne tylko dla projektów WPF)  
  
 ![](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png "f5b13c66-d918-4141-8a16-bd8f8628687a")  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z elementami w Projektancie XAML](../designers/working-with-elements-in-xaml-designer.md)   
 [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
