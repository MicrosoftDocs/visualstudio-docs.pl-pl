---
title: 'Instrukcje: Dodawanie kontrolek XMLNodes do dokumentów programu Word'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 95fc165c1a3123d68529f6ccaea99fea963c2a67
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543497"
---
# <a name="how-to-add-xmlnodes-controls-to-word-documents"></a>Instrukcje: Dodawanie kontrolek XMLNodes do dokumentów programu Word
  **Ważne** Informacje przedstawione w tym temacie dotyczące programu Microsoft Word są prezentowane wyłącznie na korzyść i użytkowanie przez osoby i organizacje, które znajdują się poza Stany Zjednoczoneą i jej terytoriami, lub opracowywaniem programów, które są uruchamiane w programie Microsoft Word, które zostały licencjonowane przez firmę Microsoft przed 2010 stycznia, gdy firma Microsoft usunie implementację konkretnych funkcji związanych z niestandardowym kodem XML z programu Microsoft Word. Te informacje dotyczące programu Microsoft Word mogą nie być odczytane lub używane przez osoby lub organizacje w Stany Zjednoczone lub na terytoriach, którzy korzystają z programu lub opracowywania programów, które są uruchamiane w programie, produkty Microsoft Word, które zostały licencjonowane przez firmę Microsoft po 10 stycznia 2010; te produkty nie będą działać tak samo jak produkty licencjonowane przed tą datą lub zakupione i licencjonowane do użycia poza Stany Zjednoczone.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Po zmapowaniu elementu powtarzalnego schematu XML do dokumentu programu Microsoft Office Word, program Visual Studio automatycznie dodaje <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolkę do dokumentu.

 Aby uzyskać informacje o mapowaniu niepowtarzalnych elementów schematu XML, zobacz [jak: Dodawanie formantów XMLNode do dokumentów programu Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).

> [!NOTE]
> <xref:Microsoft.Office.Tools.Word.XMLNodes>Formant nie jest dostępny z **przybornika** lub okna **źródła danych** , ani nie może być tworzony programowo.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-an-xmlnodes-control-to-a-document"></a>Aby dodać formant XMLNodes do dokumentu

1. W dokumencie programu Visual Studio Designer na wstążce kliknij kartę **deweloper** .

    > [!NOTE]
    > Jeśli karta **deweloper** nie jest widoczna, należy ją najpierw pokazać. Aby uzyskać więcej informacji, zobacz [jak: wyświetlić kartę Deweloper na Wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

2. W grupie **XML** kliknij pozycję **schemat**.

     Zostanie otwarte okno dialogowe **Szablony i dodatki** .

3. Kliknij kartę **schemat XML** .

4. Kliknij pozycję **Dodaj schemat**.

     Zostanie otwarte okno dialogowe **Dodaj schemat** .

5. Wybierz schemat XML zawierający powtarzające się elementy schematu, a następnie kliknij przycisk **Otwórz**.

     Zostanie wyświetlone okno dialogowe **Ustawienia schematu** .

6. Przypisz alias lub kliknij przycisk **OK** , aby dodać schemat bez aliasu.

     Schemat zostanie dodany do okna dialogowego **Dodaj schemat** .

7. W oknie dialogowym **Dodaj schemat** kliknij przycisk **OK**.

     Zostanie otwarte okienko zadań **Struktura XML** .

8. Kliknij powtarzający się element schematu w okienku zadań **Struktura XML** , aby dodać go do dokumentu.

     <xref:Microsoft.Office.Tools.Word.XMLNodes>Kontrolka jest tworzona i dodawana do projektu.

## <a name="see-also"></a>Zobacz też
- [Formant XMLNodes](../vsto/xmlnodes-control.md)
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
