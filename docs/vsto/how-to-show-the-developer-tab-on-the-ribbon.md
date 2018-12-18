---
title: 'Porady: pokazywanie karty dewelopera na Wstążce'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: edcbcb969e45403d9ca138b259073e3cf4d73be0
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349627"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Porady: pokazywanie karty dewelopera na Wstążce
  Aby uzyskać dostęp do **Developer** karty na Wstążce aplikacji pakietu Office, musisz skonfigurować je, aby pokazywała tę kartę, ponieważ nie jest wyświetlane domyślnie. Na przykład musisz wyświetlić tę kartę, jeśli chcesz dodać <xref:Microsoft.Office.Tools.Word.GroupContentControl> do dostosowywania poziomie dokumentu dla programu Word.  
  
> [!NOTE]  
>  Niniejsze wytyczne mają zastosowanie do pakietu Office 2010 lub nowszej tylko aplikacji. Jeśli chcesz wyświetlić tę kartę w pakietu Microsoft Office 2007, zobacz następującą wersję tego tematu [jak: wyświetlić kartę Deweloper na wstążce](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Dostęp nie ma **Developer** kartę.  
  
## <a name="to-show-the-developer-tab"></a>Aby wyświetlić kartę Deweloper  
  
1.  Uruchom dowolną z aplikacji pakietu Office obsługiwaną przez ten temat. Zobacz **ma zastosowanie do:** Uwaga zamieszczona wcześniej w tym temacie.  
  
2.  Na **pliku** kartę, wybrać **opcje** przycisku.  
  
     Poniższy rysunek przedstawia **pliku** kartę i **opcje** przycisku w pakiecie Office 2010.  
  
     ![Wybranie pliku, opcje w programie Outlook 2010](../vsto/media/vsto-office-file-tab.png "wybranie pliku, opcje w programie Outlook 2010")  
  
     Poniższy rysunek przedstawia **pliku** kartę w programie Office 2013.  
  
     ![Karta plik w programie Outlook 2013](../vsto/media/vsto-office2013-filetab.png "karta plik w programie Outlook 2013")  
  
     Poniższy rysunek przedstawia **opcje** przycisku w programie Office 2013.  
  
     ![Przycisk Opcje w Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "przycisk Opcje w Outlook 2013 Preview")  
  
3.  W _ApplicationName_**opcje** okna dialogowego wybierz **Dostosowywanie wstążki** przycisku.  
  
     Poniższy rysunek przedstawia **opcje** okno dialogowe i **Dostosowywanie wstążki** przycisku w programie Excel 2010. Lokalizacja tego przycisku jest podobna we wszystkich innych aplikacjach wymienionych w sekcji "Dotyczy" w górnej części tego tematu.  
  
     ![Dostosowany przycisk wstążki](../vsto/media/vsto-office2010-customizeribbonbutton.png "dostosowany przycisk wstążki")  
  
4.  Na liście głównych zakładek, wybierz **Developer** pole wyboru.  
  
     Poniższy rysunek przedstawia **Developer** pole wyboru w programie Word 2010 oraz [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. Lokalizacja tego pola wyboru jest podobna we wszystkich innych aplikacjach wymienionych w sekcji "Dotyczy" w górnej części tego tematu.  
  
     ![Pole wyboru Deweloper w oknie dialogowym Opcje programu Word](../vsto/media/vsto-office2010-developercheckbox.png "pole wyboru Deweloper w oknie dialogowym Opcje programu Word")  
  
5.  Wybierz **OK** przycisk, aby zamknąć **opcje** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz także  
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)  
  
  