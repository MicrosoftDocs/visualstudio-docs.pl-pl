---
title: 'Instrukcje: Dodawanie formantów XMLNode do dokumentów programu Word'
description: Zapoznaj się z tym, że po zmapowaniu niepowtarzalnego elementu schematu XML do dokumentu programu Microsoft Office Word, program Visual Studio automatycznie doda do dokumentu formant XMLNode.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8b9deb6732552a827cb89465f6521bc566e8c46f
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846743"
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>Instrukcje: Dodawanie formantów XMLNode do dokumentów programu Word
  **Ważne** Informacje przedstawione w tym temacie dotyczące programu Microsoft Word są prezentowane wyłącznie na korzyść i użytkowanie przez osoby i organizacje, które znajdują się poza Stany Zjednoczoneą i jej terytoriami, lub opracowywaniem programów, które są uruchamiane w programie Microsoft Word, które zostały licencjonowane przez firmę Microsoft przed 2010 stycznia, gdy firma Microsoft usunie implementację konkretnych funkcji związanych z niestandardowym kodem XML z programu Microsoft Word. Te informacje dotyczące programu Microsoft Word mogą nie być odczytane lub używane przez osoby lub organizacje w Stany Zjednoczone lub na terytoriach, którzy korzystają z programu lub opracowywania programów, które są uruchamiane w programie, produkty Microsoft Word, które zostały licencjonowane przez firmę Microsoft po 10 stycznia 2010; te produkty nie będą działać tak samo jak produkty licencjonowane przed tą datą lub zakupione i licencjonowane do użycia poza Stany Zjednoczone.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Po zmapowaniu niepowtarzalnego elementu schematu XML do Microsoft Office dokumentu programu Word, program Visual Studio automatycznie dodaje <xref:Microsoft.Office.Tools.Word.XMLNode> kontrolkę do dokumentu. Aby uzyskać informacje dotyczące mapowania powtarzających się elementów schematu XML, zobacz [How to: Add XMLNodes to Word Documents](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md).

> [!NOTE]
> <xref:Microsoft.Office.Tools.Word.XMLNode>Formant nie jest dostępny z **przybornika** lub okna **źródła danych** i nie można go utworzyć programowo.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-an-xmlnode-control-to-a-document"></a>Aby dodać formant XMLNode do dokumentu

1. W dokumencie programu Visual Studio Designer na wstążce kliknij kartę **deweloper** .

    > [!NOTE]
    > Jeśli karta **deweloper** nie jest widoczna, należy ją najpierw pokazać. Aby uzyskać więcej informacji, zobacz [jak: wyświetlić kartę Deweloper na Wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

2. W grupie **XML** kliknij pozycję **schemat**.

     Zostanie otwarte okno dialogowe **Szablony i dodatki** .

3. Kliknij kartę **schemat XML** .

4. Kliknij pozycję **Dodaj schemat**.

     Zostanie otwarte okno dialogowe **Dodaj schemat** .

5. Wybierz schemat XML zawierający niepowtarzające się elementy schematu z okna dialogowego **Dodaj schemat** , a następnie kliknij przycisk **Otwórz**.

     Zostanie wyświetlone okno dialogowe **Ustawienia schematu** .

6. Przypisz alias lub kliknij przycisk **OK** , aby dodać schemat bez aliasu.

     Schemat zostanie dodany do okna dialogowego **Dodaj schemat** .

7. W oknie dialogowym **Dodaj schemat** kliknij przycisk **OK**.

8. Zostanie otwarte okienko zadań **Struktura XML** .

9. Kliknij niepowtarzający się element schematu w okienku zadań **Struktura XML** , aby dodać go do dokumentu.

     <xref:Microsoft.Office.Tools.Word.XMLNode>Kontrolka jest tworzona i dodawana do projektu.

## <a name="see-also"></a>Zobacz także
- [XMLNode — formant](../vsto/xmlnode-control.md)
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
