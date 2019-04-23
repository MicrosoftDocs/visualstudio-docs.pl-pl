---
title: 'Instrukcje: Mapowanie schematów z arkuszami w programie Visual Studio'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ae63dd41e18b9226967b77b8adec2f45d05d9447
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60057176"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Instrukcje: Mapowanie schematów z arkuszami w programie Visual Studio
  Gdy arkusz jest otwarty w programie Visual Studio, możesz zamapować schematu XML do arkusza. Możesz użyć tych samych narzędzi Microsoft Office Excel, których używasz, gdy skoroszyt jest otwarty poza programem Visual Studio. Office project tworzy te same obiekty, czy mapowanie schematu na arkusz, przed lub po utworzeniu rozwiązania programu Excel.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
>  Nie można użyć wieloczęściowego schematów XML w rozwiązaniach programu Excel.

## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Aby zamapować schematu XML do arkusza programu Excel w programie Visual Studio

1. Otwórz projekt skoroszytem lub szablonem programu Excel w programie Visual Studio.

2. Kliknij arkusz, aby przenieść fokus do projektanta.

3. Na wstążce kliknij **Developer** kartę.

    > [!NOTE]
    >  Jeśli **Developer** karta nie jest widoczna, najpierw musisz wyświetlić. Aby uzyskać więcej informacji, zobacz [jak: Pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. W **XML** grupy, kliknij przycisk **źródła**.

     **Źródła XML** zostanie otwarte okno.

5. W **źródła XML** okna, kliknij przycisk **mapy XML**.

     **Mapy XML** zostanie otwarte okno dialogowe.

6. W **mapy XML** okno dialogowe, kliknij przycisk **Dodaj**.

7. Przejdź do pliku schematu, zaznacz go, a następnie kliknij **Otwórz**.

8. Kliknij przycisk **OK**.

     Schemat jest reprezentowana w **źródła XML** okna. W projekcie wpisane <xref:System.Data.DataSet> jest generowany na podstawie schematu, a <xref:System.Windows.Forms.BindingSource> zostanie utworzony.

9. Przeciągnij elementy z **źródła XML** okna do miejsc w arkuszu, w którym ma odpowiednie metody kontroli ma zostać utworzony.

     Jeśli przeciągniesz element schematu niepowtarzający, generuje projekt Office <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> formant, który zostanie automatycznie powiązany <xref:System.Windows.Forms.BindingSource>.

     Jeśli przeciągniesz powtarzający się element schematu, generuje projekt Office <xref:Microsoft.Office.Tools.Excel.ListObject> formant, który nie jest automatycznie powiązany ze źródłem danych. Aby uzyskać więcej informacji, zobacz [schematy XML i dane na poziomie dokumentu dostosowania](../vsto/xml-schemas-and-data-in-document-level-customizations.md).

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Mapowanie schematów z dokumentami programu Word w programie Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Schematy XML i dane dostosowywane na poziomie dokumentu](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
