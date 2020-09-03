---
title: Opcje, Edytor tekstu, C#, formatowanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting
helpviewer_keywords:
- formatting [C#]
- formatting [J#]
- Text Editor Options dialog box, formatting
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5371b7180aed462910a57daeb9bf5d43f2ecfedb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662285"
---
# <a name="options-text-editor-c-formatting"></a>Opcje, edytor tekstu, C#, formatowanie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Za pomocą okna dialogowego **Formatowanie** strony właściwości można ustawić opcje formatowania kodu w edytorze kodu. Aby uzyskać dostęp do tego okna dialogowego, kliknij opcję **Opcje** w menu **Narzędzia** , rozwiń **Edytor tekstu**, rozwiń język **C#**, a następnie kliknij pozycję **Formatowanie**.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="general-settings"></a>Ustawienia ogólne
 Ustawienia ogólne mają wpływ na to, jak edytor kodu stosuje opcje formatowania do kodu.

## <a name="uielement-list"></a>Lista elementów UI

|Etykieta|Opis|
|-----------|-----------------|
|**Automatycznie Formatuj ukończoną instrukcję na;**|Po zaznaczeniu, formatuje instrukcje po zakończeniu zgodnie z opcjami formatowania wybranymi dla edytora kodu. Wyczyść to pole, jeśli edytor kodu nie ma modyfikować instrukcji.|
|**Automatycznie Formatuj ukończony blok na}**|Po wybraniu format bloki kodu zgodnie z opcjami formatowania wybranych dla edytora kodu zaraz po zakończeniu bloku kodu. Wyczyść to pole, jeśli nie chcesz, aby Edytor kodu zmieniał bloki.|
|**Dostosuj wcięcia przy wklejaniu**|Po wybraniu formatowanie tekstu wklejonego do edytora kodu, aby dopasować opcje formatowania wybrane dla edytora kodu. Wyczyść to pole, jeśli wklejany tekst nie ma być modyfikowany.|

## <a name="preview-window"></a>Okno podglądu
 Okienka **wcięcie**, **nowe wiersze**, **odstępy**i opcje **zawijania** wyświetlają okna podglądu. Okno podglądu pokazuje efekt każdej opcji. Aby użyć okna podglądu, wybierz opcję formatowania. Okno podglądu zawiera przykład wybranej opcji. Po zmianie ustawienia, na przykład po zaznaczeniu lub usunięciu zaznaczenia pola wyboru, okno podglądu zostanie zaktualizowane, aby pokazać efekt nowego ustawienia.

## <a name="remarks"></a>Uwagi
 Opcje wcięć na stronach **kart** dla każdego języka określają, gdzie Edytor kodu umieszcza kursor po naciśnięciu klawisza Enter na końcu wiersza. Opcje wcięć w obszarze **Formatowanie** stosuje się, gdy kod jest formatowany automatycznie, na przykład podczas wklejania kodu do pliku, podczas gdy jest zaznaczona opcja **Dostosuj wcięcie przy wklejaniu** i gdy format jest pisany ręcznie.

## <a name="see-also"></a>Zobacz też
 [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
