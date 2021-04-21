---
title: Programowe kopiowanie danych i formatowanie między arkuszami
description: Dowiedz się, jak skopiować dane z zakresu na jednym arkuszu do wszystkich innych arkuszy w skoroszycie przy użyciu metody FillAcrossSheets.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0696c99e78ee1b6a7acd174e5463bbdc514fe160
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828569"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>How to: Programowe kopiowanie danych i formatowania między arkuszami
  Możesz skopiować dane z zakresu na jednym arkuszu do wszystkich innych arkuszy w skoroszycie przy użyciu <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> metody . Określ zakres i określ, czy chcesz skopiować dane, formatowanie, czy oba te ustawienia.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Przykład
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet44":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet44":::

## <a name="compile-the-code"></a>Kompilowanie kodu
 Ten przykład wymaga zakresu o nazwie `rangeData` w arkuszu.

## <a name="see-also"></a>Zobacz też
- [Praca z arkuszami](../vsto/working-with-worksheets.md)
- [How to: Programowe dodawanie nowych arkuszy do skoroszytów](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [How to: Programowe zmienianie formatowania w wierszach arkusza zawierających zaznaczone komórki](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
