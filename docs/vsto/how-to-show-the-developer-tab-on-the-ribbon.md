---
title: 'Instrukcje: Pokaż kartę Deweloper na Wstążce'
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b6641cca4ef2288452b2f6959482b311a5b07a4
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551785"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Instrukcje: Pokaż kartę Deweloper na Wstążce
  Aby uzyskać dostęp do karty **deweloper** na Wstążce aplikacji pakietu Office, należy ją skonfigurować tak, aby wyświetlała tę kartę, ponieważ nie jest wyświetlana domyślnie. Na przykład należy wyświetlić tę kartę, jeśli chcesz dodać <xref:Microsoft.Office.Tools.Word.GroupContentControl> do dostosowania na poziomie dokumentu dla programu Word.

> [!NOTE]
> Te wskazówki dotyczą tylko aplikacji pakietu Office 2010 lub nowszych. Jeśli chcesz wyświetlić tę kartę w systemie 2007 Microsoft Office, zobacz następującą wersję tego tematu [, jak: Pokaż kartę Deweloper na Wstążce](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> Dostęp nie ma karty **deweloper** .

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-show-the-developer-tab"></a>Aby wyświetlić kartę Deweloper

1. Uruchom dowolną z aplikacji pakietu Office obsługiwaną przez ten temat. Zobacz sekcję **dotyczy:** Zanotuj wcześniej w tym temacie.

2. Na karcie **plik** wybierz przycisk **Opcje** .

     Na poniższej ilustracji przedstawiono kartę **plik** i przycisk **Opcje** w pakiecie Office 2010.

     ![Wybieranie pliku, opcje w programie Outlook 2010](../vsto/media/vsto-office-file-tab.png "Wybieranie pliku, opcje w programie Outlook 2010")

     Na poniższej ilustracji przedstawiono kartę **plik** w pakiecie Office 2013.

     ![Karta plik w programie Outlook 2013](../vsto/media/vsto-office2013-filetab.png "Karta plik w programie Outlook 2013")

     Poniższy rysunek przedstawia przycisk **Opcje** w pakiecie Office 2013.

     ![Przycisk Opcje w programie Outlook 2013 (wersja] zapoznawcza) (../vsto/media/vsto-office2013-optionsbutton.png "Przycisk Opcje w programie Outlook 2013 (wersja") zapoznawcza)

3. W oknie dialogowym**Opcje** _ApplicationName_wybierz przycisk **Dostosuj Wstążkę** .

     Na poniższej ilustracji przedstawiono okno dialogowe **Opcje** i przycisk **Dostosuj Wstążkę** w programie Excel 2010. Lokalizacja tego przycisku jest podobna we wszystkich innych aplikacjach wymienionych w sekcji "dotyczy" w górnej części tego tematu.

     ![Przycisk Dostosuj Wstążkę](../vsto/media/vsto-office2010-customizeribbonbutton.png "Przycisk Dostosuj Wstążkę")

4. Na liście głównych kart, zaznacz pole wyboru **deweloper** .

     Poniższy rysunek przedstawia pole wyboru **deweloper** w programie Word 2010 i [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. Lokalizacja tego pola wyboru jest podobna we wszystkich innych aplikacjach wymienionych w sekcji "dotyczy" w górnej części tego tematu.

     ![Pole wyboru Deweloper w oknie dialogowym Opcje programu Word](../vsto/media/vsto-office2010-developercheckbox.png "Pole wyboru Deweloper w oknie dialogowym Opcje programu Word")

5. Wybierz przycisk **OK** , aby zamknąć okno dialogowe **Opcje** .

## <a name="see-also"></a>Zobacz także
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
