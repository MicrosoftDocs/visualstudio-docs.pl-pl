---
title: 'Instrukcje: mapowanie schematów do arkuszy w programie Visual Studio'
description: Dowiedz się, jak można zmapować schemat XML do Microsoft Office arkusza programu Excel, gdy arkusz jest otwarty w programie Visual Studio.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0e6d868655e3f697a7f659064026929568f2e400
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900850"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Instrukcje: mapowanie schematów do arkuszy w programie Visual Studio
  Możesz zmapować schemat XML do arkusza, gdy arkusz jest otwarty w programie Visual Studio. Używasz tych samych Microsoft Office narzędzi programu Excel, które są używane, gdy skoroszyt jest otwarty poza programem Visual Studio. Projekt pakietu Office tworzy te same obiekty niezależnie od tego, czy schemat jest mapowany do arkusza przed lub po utworzeniu rozwiązania programu Excel.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Nie można używać wieloczęściowych schematów XML w rozwiązaniach programu Excel.

## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Aby zmapować schemat XML do arkusza programu Excel w programie Visual Studio

1. Otwórz skoroszyt programu Excel lub szablon projektu w programie Visual Studio.

2. Kliknij arkusz, aby przenieść fokus do projektanta.

3. Na wstążce kliknij kartę **deweloper** .

    > [!NOTE]
    > Jeśli karta **deweloper** nie jest widoczna, należy ją najpierw pokazać. Aby uzyskać więcej informacji, zobacz [jak: wyświetlić kartę Deweloper na Wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. W grupie **XML** kliknij pozycję **Źródło**.

     Zostanie otwarte okno **Źródło XML** .

5. W oknie **Źródło XML** kliknij pozycję **mapy XML**.

     Zostanie otwarte okno dialogowe **mapy XML** .

6. W oknie dialogowym **mapy XML** kliknij przycisk **Dodaj**.

7. Przejdź do pliku schematu, zaznacz go, a następnie kliknij przycisk **Otwórz**.

8. Kliknij przycisk **OK**.

     Schemat jest reprezentowany w oknie **Źródło XML** . W projekcie typ <xref:System.Data.DataSet> jest generowany na podstawie schematu i <xref:System.Windows.Forms.BindingSource> jest tworzony.

9. Przeciągnij elementy z okna **Źródło XML** do miejsc w arkuszu, w których chcesz utworzyć odpowiednie kontrolki.

     Jeśli przeciągniesz niepowtarzający się element schematu, projekt pakietu Office wygeneruje <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> formant, który jest automatycznie powiązany z <xref:System.Windows.Forms.BindingSource> .

     Jeśli przeciągniesz powtarzający się element schematu, projekt pakietu Office wygeneruje <xref:Microsoft.Office.Tools.Excel.ListObject> formant, który nie jest automatycznie powiązany ze źródłem danych. Aby uzyskać więcej informacji, zobacz [schematy XML i dane w obszarze dostosowania na poziomie dokumentu](../vsto/xml-schemas-and-data-in-document-level-customizations.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: mapowanie schematów do dokumentów programu Word w programie Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Schematy XML i dane w dostosowaniach na poziomie dokumentu](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
