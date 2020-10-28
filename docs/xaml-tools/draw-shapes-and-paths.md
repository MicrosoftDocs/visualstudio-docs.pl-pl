---
title: Rysowanie kształtów i ścieżek
description: Użyj funkcji projektant XAML w Blend for Visual Studio, aby rysować ścieżki i kształty, modyfikować je i łączyć.
ms.custom: SEO-VS-2020
titleSuffix: Blend for Visual Studio
ms.date: 09/22/2020
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c29e2a4718a10193a4c86d1485549ded6ae2c0e
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796800"
---
# <a name="draw-shapes-and-paths"></a>Rysowanie kształtów i ścieżek

W projektant XAML *kształt* jest dokładnie to, czego oczekujesz. Na przykład: prostokąt, okrąg lub Elipsa. *Ścieżka* jest bardziej elastyczną wersją kształtu. Można wykonywać inne czynności, takie jak zmiana kształtu lub łączenie ich ze sobą w celu utworzenia nowych kształtów.

Kształty i ścieżki używają grafiki wektorowej, dzięki czemu są one skalowane do wyświetlania o wysokiej rozdzielczości.

## <a name="draw-a-shape"></a>Rysowanie kształtu

Znajdź kształty w oknie **składniki** .

:::image type="content" source="media/blend-shapes.png" alt-text="Zrzut ekranu przedstawiający kategorię Shapes okna Assets w Blend for Visual Studio":::

Przeciągnij dowolny kształt, który chcesz umieścić w obszarze kompozycji. Następnie użyj uchwytów na kształcie do skalowania, obracania, przenoszenia lub pochylania kształtu.

![Handles](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png)

## <a name="draw-a-path"></a>Rysowanie ścieżki

Ścieżka to Seria połączonych linii i krzywych. Użyj ścieżki, aby utworzyć interesujące kształty, które nie są dostępne w oknie **zasoby** .

Ścieżkę można narysować przy użyciu linii, pióra lub ołówka. Te narzędzia można znaleźć w oknie **Narzędzia** .

### <a name="draw-a-straight-line"></a>Rysowanie prostej

Użyj narzędzia **pióro** lub narzędzia **wiersza** .

**Korzystanie z narzędzia Pióro**

W obszarze kompozycji kliknij raz, aby zdefiniować punkt początkowy, a następnie kliknij przycisk ponownie, aby zdefiniować koniec wiersza.

**Korzystanie z narzędzia wiersza**

W obszarze kompozycji przeciągnij kursor od miejsca, w którym chcesz uruchomić linię, a następnie zwolnij w punkcie, w którym ma się zakończyć linia.

### <a name="draw-a-curve"></a>Rysowanie krzywych

Użyj narzędzia **pióro** .

W obszarze kompozycji kliknij raz, aby zdefiniować punkt początkowy wiersza, a następnie kliknij i przeciągnij wskaźnik, aby utworzyć odpowiednią krzywą.

Jeśli chcesz zamknąć ścieżkę, kliknij pierwszy punkt w wierszu.

### <a name="change-the-shape-of-a-curve"></a>Zmiana kształtu krzywej

Użyj narzędzia **Zaznaczanie bezpośrednie** .

Kliknij kształt, a następnie przeciągnij dowolny punkt na kształcie, aby zmienić kształt krzywej.

### <a name="draw-a-free-form-path"></a>Rysowanie ścieżki dowolnej

Użyj narzędzia **ołówek** .

W obszarze kompozycji narysuj bezpłatną ścieżkę, tak jak w przypadku użycia rzeczywistego ołówka.

### <a name="remove-part-of-a-path"></a>Usuń część ścieżki

Użyj narzędzia **Zaznaczanie bezpośrednie** .

Wybierz ścieżkę zawierającą segment, który chcesz usunąć, a następnie kliknij przycisk **Usuń** .

### <a name="remove-a-point-in-a-path"></a>Usuwanie punktu w ścieżce

Użyj narzędzia **Zaznaczanie** , aby wybrać ścieżkę. Następnie za pomocą narzędzia **pióro** kliknij punkt, który chcesz usunąć.

### <a name="add-a-point-to-a-path"></a>Dodawanie punktu do ścieżki

Użyj narzędzia **Zaznaczanie** , aby wybrać ścieżkę. Za pomocą narzędzia **pióro** kliknij w dowolnym miejscu ścieżki, w której chcesz dodać punkt.

## <a name="convert-a-shape-to-a-path"></a>Konwertowanie kształtu do ścieżki

Aby zmodyfikować kształt w taki sam sposób, jak w przypadku modyfikacji ścieżki, Przekształć kształt na ścieżkę. Zaznacz kształt, a następnie wybierz pozycję **Formatuj**  >  **ścieżkę**  >  **Konwersja do ścieżki** .

**Obejrzyj krótkie wideo:** ![ Skonfiguruj zainstalowane funkcje ](../designers/media/bldadminconsoleinitialconfigicon.png) [pracujące z ścieżkami: Przekształć kształt na ścieżkę](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).

> [!NOTE]
> **Konwersja do ścieżki** nie jest obecnie dostępna dla aplikacji platformy UWP, które mają co najmniej `TargetPlatformVersion` 10.0.16299.0 lub nowszą wersję.

## <a name="combine-paths"></a>Połącz ścieżki

Ścieżki i kształty można łączyć w jedną ścieżkę.

![Połącz ścieżki](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png)

|Liczba|Akcja|
|-|-|
|![Dwa kształty przed połączeniem](../designers/media/b1_1.png)|Dwa kształty przed połączeniem|
|![Jednostka](../designers/media/b1_2.png)|Jednostka|
|![Dzielenie](../designers/media/b1_3.png)|Dzielenie|
|![Wspólnej](../designers/media/b1_4.png)|Wspólnej|
|![Wyklucz nakładanie](../designers/media/b1_5.png)|Wyklucz nakładanie|
|![Odejmowanie](../designers/media/b1_6.png)|Odejmowanie|

**Obejrzyj krótkie wideo:** ![ Konfigurowanie zainstalowanych funkcji ](../designers/media/bldadminconsoleinitialconfigicon.png) [pracujących ze ścieżkami: łączenie ścieżek](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).

## <a name="create-a-compound-path"></a>Utwórz ścieżkę złożoną

Po utworzeniu ścieżki złożonej wszystkie przecinające się części ścieżek są odejmowane od wyniku, a wynikowa ścieżka przyjmuje właściwości wizualizacji z najniższej ścieżki.

Ścieżkę złożoną można rozdzielić w dowolnym momencie po jej utworzeniu.

![Przerwij ścieżkę złożoną](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png)

**Obejrzyj krótkie wideo:** ![ Konfigurowanie zainstalowanych funkcji ](../designers/media/bldadminconsoleinitialconfigicon.png) [pracujących ze ścieżkami: Utwórz ścieżkę złożoną](https://www.youtube.com/watch?v=Io5bC0-nH6Q).

## <a name="create-a-clipping-path"></a>Utwórz ścieżkę przycinającą

Ścieżka przycinająca jest ścieżką lub kształtem, który jest stosowany do innego obiektu, ukrywając części maskowanego obiektu, który znajduje się poza ścieżką przycinającą.

![Ścieżka przycinająca](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png)

**Obejrzyj krótkie wideo:** ![ Konfigurowanie zainstalowanych funkcji ](../designers/media/bldadminconsoleinitialconfigicon.png) [pracujących ze ścieżkami: Utwórz ścieżkę przycinającą](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232).
