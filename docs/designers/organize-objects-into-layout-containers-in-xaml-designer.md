---
title: Organizowanie obiektów w kontenery układów w projektancie XAML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: d5c56dc477b3c788f8d5ebfee4809067c77e08e8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829312"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>Organizowanie obiektów w kontenery układów w projektancie XAML

W tym artykule opisano panele układów i formantów w Projektancie XAML.

Wyobraź sobie, gdzie ma się obiekty na stronie; obiekty, takie jak obrazy, przyciski i filmy wideo. Być może ma pojawiać się w wiersze i kolumny, w jednym wierszu w pionie lub w poziomie lub w stałym położeniu.

Po został mieli Państwo możliwość zastanów się wygląd strony, wybierz panel układu. Wszystkich stron uruchomić przy użyciu jednego, ponieważ potrzebujesz czegoś, do którego można dodać obiektów. Domyślnie jest **siatki**, ale można to zmienić.

Panele układów ułatwiają rozmieścić obiekty na stronie, ale ich nie więcej niż. One ułatwiają projektowanie dla różnych rozmiarów ekranu i rozwiązania. Jeśli użytkownicy uruchamiają aplikację, wszystko w panelu układu zmienia rozmiar do dopasowania powierzchnię ekranu urządzenia z systemem. Oczywiście jeśli nie chcesz układu w taki sposób, aby to zrobić, można zastąpić to zachowanie dla części układu lub całego układu. Właściwości height i width służy do kontrolowania, który.

## <a name="layout-panels"></a>Panele układów

Twoja strona początkowa, wybierając jedną z tych paneli układu. Strona może mieć więcej niż jeden. Na przykład możesz zacząć od **siatki** Układ panelu, a następnie dodaj **StackPanel** do obszaru w **siatki** , dzięki czemu można rozmieścić formanty w pionie w tym elemencie.

Poniższe panele układów to najbardziej co jest często używane, ale istnieją inne osoby. Można je znaleźć w **zasoby** panelu.

- [Siatka](#Grid)

- [UniformGrid](#UniformGrid)

- [Kanwa](#Canvas)

- [StackPanel](#stackpanel)

- [WrapPanel](#wrappanel)

- [DockPanel](#dockpanel)

### <a name="grid"></a>Siatka

Rozmieść obiekty w wiersze i kolumny.

![Panel układu siatki](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png)

### <a name="uniformgrid"></a>UniformGrid

Rozmieść obiekty w regionach równym lub jednolite, siatki. Ten panel to idealne narzędzie do porządkowanie listy obrazów.

![Panel układu UniformGrid](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png)

(Dostępne tylko dla projektów WPF).

### <a name="canvas"></a>Kanwa

Rozmieść obiekty w jakikolwiek sposób, który ma. Jeśli użytkownicy uruchamiają aplikację, te elementy zostaną stałe pozycje, na ekranie.

![Panelu układu canvas](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png)

### <a name="stackpanel"></a>StackPanel

Rozmieść obiekty w jednym wierszu, poziomo czy pionowo.

![Panelu układu StackPanel](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png)

### <a name="wrappanel"></a>WrapPanel

Rozmieść obiekty sekwencyjnie od lewej do prawej. Gdy zespół zabraknie miejsca przy prawej krawędzi, jego *opakowuje* zawartość do następnego wiersza, i tak dalej od lewej do prawej, od góry do dołu. Można również ustawić orientacja zawijanego panelu pionie, tak aby obiekty przepływu od góry do dołu i od lewej do prawej.

(Dostępne tylko dla projektów WPF).

![Panelu układu WrapPanel](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png)

### <a name="dockpanel"></a>DockPanel

Rozmieszczanie obiektów, więc, że pozostają, lub *zadokować*, jednej krawędzi panelu.

(Dostępne tylko dla projektów WPF).

![Panelu układu DockPanel](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png)

**Obejrzyj krótki film wideo:** ![Przycisk odtwarzania](../designers/media/bldadminconsoleinitialconfigicon.PNG) [WPF — DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)

## <a name="layout-controls"></a>Formanty układu

Możesz dodać obiekty do układu kontrolek także. Nie są one jako wiele funkcji, jak panel układu, ale mogą je znaleźć przydatne w niektórych scenariuszach.

Następujące elementy sterujące układu są najbardziej popularne, ale istnieją inne osoby. Można je znaleźć w **zasoby** panelu.

- [Obramowanie](#Border)

- [Popup](#Popup)

- [ScrollViewer](#scrollviewer)

- [Okno widoku](#viewbox)

### <a name="border"></a>Obramowanie

Utwórz obramowanie i/lub tło wokół obiektu. Można dodawać tylko jednego obiektu do **obramowania**. Jeśli chcesz zastosować krawędzi i tła dla więcej niż jednego obiektu, Dodaj panelu układu, aby **obramowania**. Następnie należy dodać obiekty do tego panel lub kontrolka.

![Formant układu obramowania](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png)

### <a name="popup"></a>Okno podręczne

Pokaż informacje lub użytkownikom w oknie opcji. Można dodawać tylko jednego obiektu do **okno podręczne**. Domyślnie **okno podręczne** zawiera **siatki** , ale można ją zamienić.

### <a name="scrollviewer"></a>ScrollViewer

Pozwalają użytkownikom na przewiń w dół strony lub części strony. Można dodawać tylko jednego obiektu do **ScrollViewer** dzięki temu jest bardzo rozsądne, aby dodać panel układu, takich jak **siatki** lub **StackPanel**.

![Scrollviewer — formant układu](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png)

### <a name="viewbox"></a>Okno widoku

Skalowanie obiektów, podobnie jak w przypadku Kontrolka powiększenia. Można dodawać tylko jednego obiektu do **Viewbox**. Jeśli chcesz zastosować ten efekt do więcej niż jednego obiektu, Dodaj panelu układu, aby **ViewBox**, a następnie dodać kontrolki do panelu układów.

(Dostępne tylko dla projektów WPF).

![Formant okna widoku układu](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png)

## <a name="see-also"></a>Zobacz także

- [Praca z elementami w projektancie XAML](../designers/working-with-elements-in-xaml-designer.md)
- [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)