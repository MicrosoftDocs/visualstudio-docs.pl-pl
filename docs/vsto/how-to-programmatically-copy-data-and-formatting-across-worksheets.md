---
title: Programistyczne kopiowanie danych i formatowania w arkuszach
description: Dowiedz się, jak kopiować dane z zakresu na jednym arkuszu do wszystkich arkuszy w skoroszycie przy użyciu metody FillAcrossSheets.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cdcae80148e54f2e1adb09d4c69b2dc3268b7428
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523192"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Instrukcje: Programowane kopiowanie danych i formatowania w arkuszach
  Dane można kopiować z zakresu na jednym arkuszu do wszystkich arkuszy w skoroszycie przy użyciu <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> metody. Określ zakres oraz to, czy chcesz kopiować dane, formatowanie czy oba elementy.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Przykład
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład wymaga zakresu o nazwie `rangeData` w arkuszu.

## <a name="see-also"></a>Zobacz też
- [Pracuj z arkuszami](../vsto/working-with-worksheets.md)
- [Instrukcje: Programowane dodawanie nowych arkuszy do skoroszytów](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Instrukcje: Programowane zmienianie formatowania w wierszach arkusza zawierających zaznaczone komórki](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
