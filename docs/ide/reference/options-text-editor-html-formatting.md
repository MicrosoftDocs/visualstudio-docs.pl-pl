---
title: Opcje, Edytor tekstu, HTML (Formularze sieci Web), Formatowanie
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Format
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e28caf7f71af7c7a07634d1732a1001a32a4aee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568324"
---
# <a name="options-text-editor-html-web-forms-formatting"></a>Opcje, Edytor tekstu, HTML (Formularze sieci Web), Formatowanie

Strona Opcje **formatowania** służy do ustawiania opcji projektu HTML dla formatowania kodu w Edytorze kodów. Aby uzyskać dostęp do tej strony, na pasku menu wybierz pozycję**Opcje** **narzędzi** > , a następnie rozwiń pozycję**Formatowanie**HTML **edytora** > **tekstu HTML (Formularze sieci Web).** > 

## <a name="capitalization"></a>Wielkości liter

Po wybraniu tych opcji edytory Widok źródłowy i XML stosują domyślny format liter do nazw elementów i atrybutów podczas pierwszego tworzenia elementów i podczas automatycznego formatowania. Ustawienia **Zastosuj automatyczne formatowanie** określają czas automatycznego formatowania.

> [!WARNING]
> W formacie XML rozróżniana jest wielkość liter. Ustawienie przypadku domyślnego może mieć wpływ na analizatory XML.

### <a name="uielement-list"></a>Lista UIElement

**Tag serwera, atrybuty serwera**

Te opcje określają sposób oznaczania znaczników dla formantów serwera sieci Web.

|Opcja|Wynik|
|---------------------------------|------------------------------|
|**Jak wprowadzono**|Przypadek elementu jest dokładnie taki, jak ją wprowadzasz.|
|**Wielkie litery**|Nazwy elementów są sformatowane na wielkie litery.|
|**Małe litery**|Nazwy elementów są sformatowane do małych liter.|
|**Definicja zestawu**|Wielkość elementu jest określana przez sposób definiowania elementu w odpowiedniej klasie typu.|

**Tag klienta, atrybuty klienta**

Opcje te określają, czy automatyczne formatowanie zmienia nazwy atrybutów HTML i właściwości na wielkie lub małe litery, czy zachowuje je jako wprowadzone.

|Opcja|Wynik|
|---------------------------------|------------------------------|
|**Jak wprowadzono**|Przypadek atrybutu jest dokładnie taki, jak ją wprowadzasz.|
|**Wielkie litery**|Nazwy atrybutów są sformatowane na wielkie litery.|
|**Małe litery**|Nazwy atrybutów są sformatowane na małe litery.|

## <a name="automatic-formatting-options"></a>Opcje automatycznego formatowania

Te opcje powodują, że edytor widoku źródło dodawania lub usuwania fizycznych podziałów wierszy podczas automatycznego formatowania. Można również określić, czy edytor dodaje cudzysłowy wokół atrybutów.

> [!NOTE]
> Te ustawienia nie zmieniają odstępu w znacznikach XML.

### <a name="uielement-list"></a>Lista UIElement

- **Wstawianie cudzysłowów wartości atrybutu podczas wpisywania**

   Gdy ta opcja jest zaznaczona, edytor automatycznie umieszcza znaki cudzysłowu wokół atrybutów podczas pisania (na przykład: ID="Select1"). Wyczyść tę opcję, jeśli wolisz ręcznie wstawić cudzysłowy do znaczników.

   > [!NOTE]
   > Niezależnie od tego, czy ta opcja jest zaznaczona, wszystkie istniejące cudzysłowy w znacznikach są zachowywane; cudzysłowów nigdy nie są usuwane.

- **Wstawianie cudzysłowów wartości atrybutu podczas formatowania**

   Gdy ta opcja jest zaznaczona, formatowanie automatyczne dodaje znaki cudzysłowu wokół wartości atrybutów (na przykład: ID="Select1").

   > [!NOTE]
   > Niezależnie od tego, czy ta opcja jest zaznaczona, wszystkie istniejące cudzysłowy w znacznikach są zachowywane.

- **Automatyczne wstawianie znacznika zamknięcia**

   Gdy ta opcja jest zaznaczona, edytor automatycznie tworzy znacznik zamykający (na przykład ** \</b>**) po zamknięciu znacznika otwierającego.

## <a name="tag-wrapping"></a>Zawijanie znaczników

Te opcje określają, czy edytor dzieli tagi na wiersze, jeśli wykraczają one poza pewną długość.

### <a name="uielement-list"></a>Lista UIElement

- **Zawijania znaczników po przekroczeniu określonej długości**

   Gdy ta opcja jest zaznaczona, edytor dzieli znaczniki między wierszami, jeśli znacznik wykracza poza długość określoną w polu tekstowym **Długość.** Ta akcja występuje tylko podczas formatowania znacznika, a nie podczas wpisywania nowego tagu.

   > [!NOTE]
   > Określona wartość jest używana jako wartość minimalna. Edytor nie rozbija poszczególnych atrybutów.

- **Długość**

   Określa liczbę znaków wyświetlanych w wierszu przed zawijaniem. To pole wprowadzania jest wyłączone, chyba że **pole Wrap tagów po przekroczeniu określonej długości** pole jest zaznaczone.

- **Opcje specyficzne dla znaczników**

   Wyświetla okno dialogowe **Opcje specyficzne dla znaczników,** w którym można ustawić opcje formatowania dla poszczególnych tagów lub grup znaczników.

## <a name="see-also"></a>Zobacz też

- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
