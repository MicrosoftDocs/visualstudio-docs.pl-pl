---
title: Niestandardowe akcje w regionach formularzy programu Outlook
description: Dowiedz się, w jaki sposób przyciski wyświetlania akcji, takie jak Odpowiedz i Odpowiedz wszystkim, umożliwiają użytkownikom reagowanie na Microsoft Office elementu Outlook.
ms.custom: SEO-VS-2020
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4fe77cddcfe810e73d13de81cc7280969c1d1b1c
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848199"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Niestandardowe akcje w regionach formularzy programu Outlook
  Akcje Wyświetla przyciski umożliwiające użytkownikom odpowiadanie na Microsoft Office element programu Outlook. Na przykład aby odpowiedzieć na element poczty e-mail, użytkownicy klikają przyciski **Odpowiedz**, **Odpowiedz wszystkim** lub **Prześlij dalej** . Każda z tych akcji tworzy nowy element poczty i wypełnia pola elementu przy użyciu informacji z oryginalnego elementu.

 Można utworzyć akcję niestandardową, która otwiera dowolny rodzaj elementu programu Outlook. Na przykład można dodać akcję niestandardową, która otwiera nowy termin lub element zadania. Ustaw właściwości akcji niestandardowej lub użyj kodu niestandardowego, aby wypełnić pola nowego elementu. Akcje niestandardowe są wyświetlane na liście rozwijanej **Akcje niestandardowe** elementu, który jest otwarty w oknie Inspektora programu Outlook.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-custom-actions-to-a-form-region"></a>Dodawanie akcji niestandardowych do regionu formularza
 Aby dodać akcję niestandardową do regionu formularza, użyj okna dialogowego **Akcje niestandardowe** . Możesz otworzyć okno dialogowe **Akcje niestandardowe** , wybierając region formularza w **Eksplorator rozwiązań**, rozszerzając węzeł **manifestu** w **oknie właściwości**, wybierając Właściwość **CustomActions** , a następnie klikając przycisk wielokropka (![ASP.net Mobile Designer](../sharepoint/media/mwellipsis.gif "Wielokropek projektanta ASP.NET Mobile")).

 Możesz użyć okna dialogowego **Akcje niestandardowe** , aby określić *formularz docelowy*. Formularz docelowy jest formularz, który pojawia się, gdy użytkownik wykonuje akcję niestandardową.

 Możesz również użyć okna dialogowego **Akcje niestandardowe** , aby określić, jak informacje z oryginalnego elementu mają być wyświetlane w formularzu docelowym.

 W poniższej tabeli opisano właściwości, które są dostępne w oknie dialogowym **Akcje niestandardowe** .

|Właściwość|Opis|
|--------------|-----------------|
|**AddressLike**|Określa sposób, w jaki zostanie rozkierowany formularz docelowy.|
|**Treść**|Określa sposób, w jaki treść oryginalnego elementu jest dołączana do formularza docelowego.|
|**Włączono**|Wskazuje, czy akcja niestandardowa jest włączona. Jeśli ta właściwość ma wartość **Fałsz**, Akcja niestandardowa zostanie wyłączona.|
|**Metoda**|Określa typ odpowiedzi dostępnej podczas wykonywania akcji niestandardowej. Akcja niestandardowa umożliwia wysłanie formularza, otwarcie formularza lub wyświetlenie monitu o potwierdzenie lub otwarcie formularza.|
|**Nazwa**|Określa nazwę wewnętrzną, która może być używana do odwoływania się do tej akcji niestandardowej w kodzie.|
|**ShowOnRibbon**|Wskazuje, czy akcja niestandardowa ma być wyświetlana na Wstążce oryginalnego elementu.|
|**SubjectPrefix**|Określa tekst wstawiany na początku wiersza tematu formularza docelowego.|
|**TargetForm**|Określa nazwę klasy komunikatu w formularzu docelowym. Na przykład wpisz **IPM. Zadanie** umożliwiające otwarcie formularza zadania.|
|**Tytuł**|Określa etykietę przycisku akcji niestandardowej.|

## <a name="customize-a-custom-action-at-run-time"></a>Dostosuj akcję niestandardową w czasie wykonywania
 Możesz również dodać zachowanie do akcji niestandardowej przy użyciu kodu. Można na przykład dodać kod, który przyjmuje nazwy adresatów poczty e-mail i dodaje te nazwy jako uczestników w nowym elemencie terminu. [W tym](/office/vba/api/Outlook.MailItem.CustomAction) celu należy obsłużyć zdarzenie " [MailItem" obiektu](/office/vba/api/Outlook.MailItem).

## <a name="see-also"></a>Zobacz także
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Przewodnik: Projektowanie regionu formularza programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
