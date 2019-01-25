---
title: 'Instrukcje: Dodawanie formantów XMLNode do dokumentów programu Word'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 1fc1f236604fa0ccd439756dc2c0b1368a534356
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868904"
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>Instrukcje: Dodawanie formantów XMLNode do dokumentów programu Word
  **Ważne** informacji zawartych w tym temacie dotyczące programu Microsoft Word jest prezentowane wyłącznie do korzyści i korzystanie z innym osobom oraz organizacjom, którzy znajdują się poza w Stanach Zjednoczonych i ich terytoriach lub korzystających z lub tworzenie programy, korzystających z produktów Microsoft Word, które są licencjonowane przez firmę Microsoft przed 2010 stycznia, po usunięciu implementację funkcji określonej przez Microsoft związane z niestandardowy kod XML z programu Microsoft Word. Te informacje dotyczące programu Microsoft Word nie mogą być odczytywane lub używane przez osoby i organizacje w Stanach Zjednoczonych lub jego terytoria, którzy za pomocą lub opracowywanie programów uruchamianych na produkty Microsoft Word, które są licencjonowane przez firmę Microsoft, po 10 stycznia 2010 r. ; te produkty będą nie działa tak samo jako produkty licencjonowane przed tą datą lub kupić i licencjonowane do użycia poza Stanami Zjednoczonymi.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Kiedy mapujesz niepowtarzający elementu schematu XML do dokumentu programu Microsoft Office Word Visual Studio automatycznie dodaje <xref:Microsoft.Office.Tools.Word.XMLNode> kontrolki do dokumentu. Aby uzyskać informacje o mapowaniu powtarzających się elementów schematu XML, zobacz [jak: Dodawanie formantów XMLNodes do dokumentów programu Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md).  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Word.XMLNode> Formant nie jest dostępny z **przybornika** lub **źródeł danych** okna, a nie można utworzyć programowo.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-an-xmlnode-control-to-a-document"></a>Aby dodać formant XMLNode do dokumentów  
  
1.  Dokument w Projektancie Visual Studio na wstążce kliknij **Developer** kartę.  
  
    > [!NOTE]  
    >  Jeśli **Developer** karta nie jest widoczna, najpierw musisz wyświetlić. Aby uzyskać więcej informacji, zobacz [jak: Pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
2.  W **XML** grupy, kliknij przycisk **schematu**.  
  
     **Szablony i dodatki** zostanie otwarte okno dialogowe.  
  
3.  Kliknij przycisk **schematu XML** kartę.  
  
4.  Kliknij przycisk **schemat Dodaj**.  
  
     **Schemat Dodaj** zostanie otwarte okno dialogowe.  
  
5.  Wybieranie schematu XML, który zawiera niepowtarzający elementy schematu z **schemat Dodaj** dialogowym i kliknij przycisk **Otwórz**.  
  
     **Schemat ustawień** pojawi się okno dialogowe.  
  
6.  Przypisać aliasu lub kliknij przycisk **OK** można dodać schematu bez aliasu.  
  
     Schemat jest dodawany do **schemat Dodaj** okno dialogowe.  
  
7.  W **schemat Dodaj** okno dialogowe, kliknij przycisk **OK**.  
  
8.  **Struktury XML** zostanie otwarte okienko zadań.  
  
9. Kliknij element schematu niepowtarzający **struktury XML** okienka zadań, aby dodać go do dokumentu.  
  
     <xref:Microsoft.Office.Tools.Word.XMLNode> Formant zostanie utworzony i dodany do projektu.  
  
## <a name="see-also"></a>Zobacz także  
 [Formant XMLNode](../vsto/xmlnode-control.md)   
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
