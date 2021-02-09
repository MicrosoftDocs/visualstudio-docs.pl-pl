---
title: Kojarzenie regionu formularza z klasą wiadomości programu Outlook
description: Dowiedz się, w jaki sposób można określić, które Microsoft Office elementy programu Outlook będą wyświetlać region formularza, kojarząc region formularza z klasą wiadomości każdego elementu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.InvalidMessageClassName
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FormRegionMessageClassAttribute
- form regions [Office development in Visual Studio], message classes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0bbbd381ff84714b780bbb817ccfea64ac05e949
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882547"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Kojarzenie regionu formularza z klasą wiadomości programu Outlook
  Można określić, które Microsoft Office elementy programu Outlook będą wyświetlać region formularza, kojarząc region formularza z klasą wiadomości każdego elementu. Na przykład jeśli chcesz dołączyć region formularza do dołu elementu poczty, możesz skojarzyć region formularza z `IPM.Note` klasą wiadomości.

 Aby skojarzyć region formularza z klasą wiadomości, określ nazwę klasy komunikatu w kreatorze **nowego regionu formularza programu Outlook** lub zastosuj atrybut do klasy fabryki regionów formularza.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="understand-outlook-message-classes"></a>Informacje o klasach wiadomości programu Outlook
 Klasa wiadomości programu Outlook identyfikuje typ elementu programu Outlook. W poniższej tabeli wymieniono osiem standardowych typów elementów i ich nazwy klas komunikatów.

|Typ elementu programu Outlook|Nazwa klasy komunikatu|
|-----------------------|------------------------|
|AppointmentItem|`IPM.Appointment`|
|ContactItem|`IPM.Contact`|
|DistListItem|`IPM.DistList`|
|JournalItem|`IPM.Activity`|
|MailItem|`IPM.Note`|
|PostItem|`IPM.Post` lub `IPM.Post.RSS`|
|TaskItem|`IPM.Task`|

 Można również określić nazwy niestandardowych klas komunikatów. Niestandardowe klasy komunikatów identyfikują formularze niestandardowe zdefiniowane w programie Outlook.

> [!NOTE]
> Dla regionów zamiany i Zamień — wszystkie regiony formularzy można określić nową niestandardową nazwę klasy wiadomości. Nie trzeba używać nazwy klasy wiadomości istniejącego formularza niestandardowego. Nazwa niestandardowej klasy wiadomości musi być unikatowa. Jednym ze sposobów upewnienia się, że nazwa jest unikatowa, jest użycie konwencji nazewnictwa podobnej do następującej: \<*StandardMessageClassName*> . \<*Company*> .\<*MessageClassName*> (na przykład: `IPM.Note.Contoso.MyMessageClass` ).

## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Kojarzenie regionu formularza z klasą wiadomości programu Outlook
 Istnieją dwa sposoby kojarzenia regionu formularza z klasą wiadomości:

- Użyj kreatora **nowego regionu formularza programu Outlook** .

- Zastosuj atrybuty klasy.

### <a name="use-the-new-outlook-form-region-wizard"></a>Korzystanie z Kreatora nowego regionu formularza programu Outlook
 Na ostatniej stronie kreatora **nowego regionu formularza programu Outlook** można wybrać standardowe klasy komunikatów i wpisać nazwy niestandardowych klas komunikatów, które mają być skojarzone z regionem formularza.

 Standardowe klasy wiadomości są niedostępne, jeśli region formularza zaprojektowano w celu zamienienia całego formularza lub domyślnej strony formularza. Można określić standardowe nazwy klas komunikatów tylko dla formularzy, które dodają nową stronę do formularza lub które są dołączane na dole formularza. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

 Aby uwzględnić co najmniej jedną niestandardową klasę wiadomości, wpisz swoje nazwy w polu, **które niestandardowe klasy komunikatów będą wyświetlać ten region formularza?**

 Wpisane nazwy muszą być zgodne z następującymi wskazówkami:

- Użyj w pełni kwalifikowanej nazwy klasy komunikatów (na przykład: "IPM. Uwaga. contoso ").

- Użyj średników do rozdzielenia wielu nazw klas komunikatów.

- Nie uwzględniaj standardowych klas wiadomości programu Outlook, takich jak "IPM. Uwaga "lub" IPM. Kontakt ". Zawierają tylko niestandardowe klasy komunikatów, takie jak "IPM. Uwaga. contoso ".

- Nie określaj podstawowej klasy wiadomości (na przykład: "IPM").

- Nazwy klas komunikatów nie mogą przekraczać 256 znaków.

  Kreator **nowego regionu formularza programu Outlook** sprawdza poprawność formatu danych wejściowych po kliknięciu przycisku **Zakończ**.

> [!NOTE]
> Kreator **nowego regionu formularza programu Outlook** nie sprawdza, czy nazwy klas komunikatów, które zostały wprowadzone, są prawidłowe lub prawidłowe.

 Po zakończeniu pracy Kreatora Kreator **nowego regionu formularza programu Outlook** zastosuje atrybuty do klasy region formularza, która zawiera określone nazwy klas komunikatów. Te atrybuty można również zastosować ręcznie.

### <a name="apply-class-attributes"></a>Zastosuj atrybuty klasy
 Po zakończeniu pracy kreatora **nowego regionu formularza programu Outlook** można skojarzyć region formularza z klasą wiadomości programu Outlook. W tym celu Zastosuj atrybuty do klasy fabryki regionów formularza.

 W poniższym przykładzie przedstawiono dwa <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> atrybuty, które zostały zastosowane do klasy fabryki regionów formularza o nazwie `myFormRegion` . Pierwszy atrybut kojarzy region formularza z klasą standardowego komunikatu dla formularza wiadomości e-mail. Drugi atrybut kojarzy region formularza z niestandardową klasą wiadomości o nazwie `IPM.Task.Contoso` .

 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]

 Atrybuty muszą być zgodne z następującymi wskazówkami:

- W przypadku niestandardowych klas komunikatów Użyj w pełni kwalifikowanej nazwy klasy komunikatów (na przykład: "IPM. Uwaga. contoso ").

- Nie określaj podstawowej klasy wiadomości (na przykład: "IPM").

- Nazwy klas komunikatów nie mogą przekraczać 256 znaków.

- Nie uwzględniaj nazw standardowych klas komunikatów, jeśli region formularza zastępuje całą formę lub stronę domyślną formularza. Można określić standardowe nazwy klas komunikatów tylko dla formularzy, które dodają nową stronę do formularza lub które są dołączane na dole formularza. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

  Program Visual Studio sprawdza poprawność formatu nazw klas komunikatów podczas kompilowania projektu.

> [!NOTE]
> Program Visual Studio nie sprawdza, czy nazwy klas komunikatów, które zostały wprowadzone są poprawne lub prawidłowe.

## <a name="see-also"></a>Zobacz też
- [Dostęp do regionu formularza w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Przewodnik: Projektowanie regionu formularza programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Wytyczne dotyczące tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Przegląd nazw formularzy i klas komunikatów](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)
- [Jak program Outlook Forms i elementy współpracują ze sobą](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)
