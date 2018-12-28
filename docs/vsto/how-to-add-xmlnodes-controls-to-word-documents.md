---
title: 'Instrukcje: Dodawanie formantów XMLNodes do dokumentów programu Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b27753590ea84fac6029bea0919a1aeda90543fa
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647139"
---
# <a name="how-to-add-xmlnodes-controls-to-word-documents"></a>Instrukcje: Dodawanie formantów XMLNodes do dokumentów programu Word
  **Ważne** informacji zawartych w tym temacie dotyczące programu Microsoft Word jest prezentowane wyłącznie do korzyści i korzystanie z innym osobom oraz organizacjom, którzy znajdują się poza w Stanach Zjednoczonych i ich terytoriach lub korzystających z lub tworzenie programy, korzystających z produktów Microsoft Word, które są licencjonowane przez firmę Microsoft przed 2010 stycznia, po usunięciu implementację funkcji określonej przez Microsoft związane z niestandardowy kod XML z programu Microsoft Word. Te informacje dotyczące programu Microsoft Word nie mogą być odczytywane lub używane przez osoby i organizacje w Stanach Zjednoczonych lub jego terytoria, którzy za pomocą lub opracowywanie programów uruchamianych na produkty Microsoft Word, które są licencjonowane przez firmę Microsoft, po 10 stycznia 2010 r. ; te produkty będą nie działa tak samo jako produkty licencjonowane przed tą datą lub kupić i licencjonowane do użycia poza Stanami Zjednoczonymi.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Kiedy mapujesz powtarzające się elementu schematu XML do dokumentu programu Microsoft Office Word Visual Studio automatycznie dodaje <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolki do dokumentu.  
  
 Aby dowiedzieć się, jak mapowanie niepowtarzający elementy schematu XML, zobacz [jak: Dodawanie formantów XMLNode do dokumentów programu Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Word.XMLNodes> Formant nie jest dostępny z **przybornika** lub **źródeł danych** okna, ani nie może być utworzony programowo.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-an-xmlnodes-control-to-a-document"></a>Aby dodać formant XMLNodes do dokumentu  
  
1.  Dokument w Projektancie Visual Studio na wstążce kliknij **Developer** kartę.  
  
    > [!NOTE]  
    >  Jeśli **Developer** karta nie jest widoczna, najpierw musisz wyświetlić. Aby uzyskać więcej informacji, zobacz [jak: Pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
2.  W **XML** grupy, kliknij przycisk **schematu**.  
  
     **Szablony i dodatki** zostanie otwarte okno dialogowe.  
  
3.  Kliknij przycisk **schematu XML** kartę.  
  
4.  Kliknij przycisk **schemat Dodaj**.  
  
     **Schemat Dodaj** zostanie otwarte okno dialogowe.  
  
5.  Wybierz schemat XML, który zawiera powtarzające się elementy schematu i kliknij przycisk **Otwórz**.  
  
     **Schemat ustawień** pojawi się okno dialogowe.  
  
6.  Przypisać aliasu lub kliknij przycisk **OK** można dodać schematu bez aliasu.  
  
     Schemat jest dodawany do **schemat Dodaj** okno dialogowe.  
  
7.  W **schemat Dodaj** okno dialogowe, kliknij przycisk **OK**.  
  
     **Struktury XML** zostanie otwarte okienko zadań.  
  
8.  Kliknij pozycję powtarzający się element schematu **struktury XML** okienka zadań, aby dodać go do dokumentu.  
  
     <xref:Microsoft.Office.Tools.Word.XMLNodes> Formant zostanie utworzony i dodany do projektu.  
  
## <a name="see-also"></a>Zobacz także  
 [Formant XMLNodes](../vsto/xmlnodes-control.md)   
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  