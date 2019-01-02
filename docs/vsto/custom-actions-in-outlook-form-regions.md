---
title: Niestandardowe akcje w regionach formularzy programu Outlook
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5f7268ed6801e06477312b47f2c890b59ba62f64
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869522"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Niestandardowe akcje w regionach formularzy programu Outlook
  Akcje wyświetlanie przycisków, które umożliwiają użytkownikom odpowiedzieć na element programu Microsoft Office Outlook. Na przykład, aby odpowiedzieć elementu poczty, użytkownik kliknie **odpowiedzi**, **Odpowiedz wszystkim**, lub **do przodu** przyciski akcji. Każda z tych akcji tworzy nowy element poczty i wypełni pola elementu przy użyciu informacji z oryginalnego elementu.  
  
 Można utworzyć niestandardową akcję, która otwiera dowolnego rodzaju elementu programu Outlook. Na przykład można dodać niestandardową akcję, która zostanie otwarty nowy element terminu lub zadania. Ustaw właściwości niestandardowej akcji lub użyj niestandardowego kodu, aby wypełnić pola nowego elementu. Akcje niestandardowe są wyświetlane w **akcje niestandardowe** listy rozwijanej elementu, który jest otwarty w oknie inspektora programu Outlook.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="add-custom-actions-to-a-form-region"></a>Dodawanie akcji niestandardowych do regionu formularza  
 Aby dodać akcję niestandardową do regionu formularza, należy użyć **akcje niestandardowe** okno dialogowe. Możesz otworzyć **akcje niestandardowe** okno dialogowe w **Eksploratora rozwiązań** , rozwijając **manifestu** węzła, wybierając **CustomActions**właściwości, a następnie klikając przycisk wielokropka (![przenośnych elipsy projektanta ASP.NET](../sharepoint/media/mwellipsis.gif "elipsy projektanta Mobile ASP.NET")).  
  
 Możesz użyć **akcje niestandardowe** okno dialogowe, aby określić *docelowe formularza*. Formularz docelowy jest formularz, który jest wyświetlany, gdy użytkownik wykonuje akcji niestandardowej.  
  
 Można również użyć **akcje niestandardowe** okno dialogowe, aby określić, jak informacje z oryginalnego elementu pojawią się w formularzu docelowym.  
  
 W poniższej tabeli opisano właściwości, które są dostępne w **akcje niestandardowe** okno dialogowe.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**AddressLike**|Określa, jak formularz docelowy problem zostanie rozwiązany.|  
|**Body**|Określa, jak treści elementu jest dołączany do formularza docelowego.|  
|**Włączone**|Wskazuje, czy włączono akcji niestandardowej. Jeśli ta właściwość jest ustawiona **false**, akcji niestandardowej jest wyłączona.|  
|**— Metoda**|Określa typ odpowiedzi jest dostępne podczas wykonywania akcji niestandardowej. Akcja niestandardowa można wysyłać formularza, otwórz formularz lub monitować użytkownika, czy chcą wysłać lub Otwórz formularz.|  
|**Nazwa**|Określa nazwę wewnętrzną, który można odwoływać się do akcji niestandardowej w kodzie.|  
|**ShowOnRibbon**|Wskazuje, czy mają być wyświetlane akcji niestandardowej na Wstążce oryginalnego elementu.|  
|**SubjectPrefix**|Określa tekst, który jest wstawiany na początku tego tematu formularza docelowego.|  
|**TargetForm**|Określa nazwę klasy wiadomości w postaci docelowego. Na przykład wpisz **IPM. Zadanie** do otwierania formularza zadania.|  
|**Tytuł**|Określa etykietę przycisk akcji niestandardowej.|  
  
## <a name="customize-a-custom-action-at-runtime"></a>Dostosuj akcję niestandardową, w czasie wykonywania  
 Można również dodać zachowania do akcji niestandardowej przy użyciu kodu. Na przykład można dodać kod, który przyjmuje nazwy adresatów wiadomości e-mail i dodaje tych nazw jako uczestnicy nowego elementu terminu. Aby to zrobić, należy obsługiwać [Akcja niestandardowa](/office/vba/api/Outlook.MailItem.CustomAction) zdarzenia [obiektu MailItem](/office/vba/api/Outlook.MailItem).  
  
## <a name="see-also"></a>Zobacz także  
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Przewodnik: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
