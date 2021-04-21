---
title: Kojarzenie regionu formularza z klasą komunikatów programu Outlook
description: Dowiedz się, jak określić, Microsoft Office elementy programu Outlook wyświetlają region formularza, kojarząc region formularza z klasą komunikatów każdego elementu.
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
ms.openlocfilehash: be3b789fabf00d853d447cb3489ef07a5b494fcd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826996"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Kojarzenie regionu formularza z klasą komunikatów programu Outlook
  Możesz określić, Microsoft Office elementy programu Outlook wyświetlają region formularza, kojarząc region formularza z klasą komunikatów każdego elementu. Jeśli na przykład chcesz dołączyć region formularza na końcu elementu poczty, możesz skojarzyć region formularza z `IPM.Note` klasą wiadomości.

 Aby skojarzyć region formularza z klasą komunikatów, określ nazwę klasy komunikatów w kreatorze Nowy region formularza programu **Outlook** lub zastosuj atrybut do klasy fabryki regionów formularzy.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="understand-outlook-message-classes"></a>Opis klas komunikatów programu Outlook
 Klasa wiadomości programu Outlook identyfikuje typ elementu programu Outlook. W poniższej tabeli wymieniono osiem standardowych typów elementów i ich nazwy klas komunikatów.

|Typ elementu programu Outlook|Nazwa klasy komunikatów|
|-----------------------|------------------------|
|AppointmentItem|`IPM.Appointment`|
|ContactItem|`IPM.Contact`|
|DistListItem|`IPM.DistList`|
|JournalItem|`IPM.Activity`|
|Mailitem|`IPM.Note`|
|PostItem|`IPM.Post` lub `IPM.Post.RSS`|
|TaskItem|`IPM.Task`|

 Można również określić nazwy niestandardowych klas komunikatów. Niestandardowe klasy komunikatów identyfikują formularze niestandardowe, które definiujesz w programie Outlook.

> [!NOTE]
> W celu zastąpienia i zastąpienia wszystkich regionów formularzy można określić nową niestandardową nazwę klasy komunikatów. Nie trzeba używać nazwy klasy komunikatów istniejącego formularza niestandardowego. Nazwa niestandardowej klasy komunikatów musi być unikatowa. Jednym ze sposobów zapewnienia, że nazwa jest unikatowa, jest użycie konwencji nazewnictwa podobnej do następującej: \<*StandardMessageClassName*> \<*Company*> .\<*MessageClassName*> (na przykład: `IPM.Note.Contoso.MyMessageClass` ).

## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Kojarzenie regionu formularza z klasą komunikatów programu Outlook
 Istnieją dwa sposoby skojarzenia regionu formularza z klasą komunikatów:

- Użyj kreatora **Nowy region formularza programu Outlook.**

- Stosowanie atrybutów klasy.

### <a name="use-the-new-outlook-form-region-wizard"></a>Korzystanie z kreatora Nowy region formularza programu Outlook
 Na ostatniej stronie kreatora Nowy region formularza programu **Outlook** możesz wybrać standardowe klasy komunikatów i wpisać nazwy niestandardowych klas komunikatów, które chcesz skojarzyć z regionem formularza.

 Standardowe klasy komunikatów nie są dostępne, jeśli region formularza został zaprojektowany w celu zastąpienia całego formularza lub domyślnej strony formularza. Standardowe nazwy klas komunikatów można określić tylko dla formularzy, które dodają nową stronę do formularza lub które są dołączane do dołu formularza. Aby uzyskać więcej informacji, [zobacz How to: Add a form region to an Outlook Add-in project](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)(Jak dodać region formularza do projektu dodatku programu Outlook).

 Aby uwzględnić co najmniej jedną niestandardową klasę komunikatów, wpisz ich nazwy w polu Które niestandardowe klasy komunikatów **będą wyświetlać ten region formularza?.**

 Wpisywane nazwy muszą być zgodne z następującymi wytycznymi:

- Użyj w pełni kwalifikowanej nazwy klasy komunikatów (na przykład: "IPM. Note.Contoso").

- Użyj średników, aby oddzielić wiele nazw klas komunikatów.

- Nie należy uwzględniać standardowych klas wiadomości programu Outlook, takich jak "IPM. Uwaga" lub "IPM. Kontakt". Uwzględnij tylko niestandardowe klasy komunikatów, takie jak "IPM. Note.Contoso".

- Nie określaj samej klasy komunikatów podstawowych (na przykład "IPM").

- Nie należy przekraczać 256 znaków dla każdej nazwy klasy komunikatów.

  Kreator **Nowy region formularza programu Outlook** weryfikuje format danych wejściowych po kliknięciu **przycisku Zakończ.**

> [!NOTE]
> Kreator **Nowy region formularza programu Outlook** nie weryfikuje, czy podana nazwa klasy komunikatów jest poprawna lub prawidłowa.

 Po zakończeniu pracy kreatora kreator New Outlook Form Region (Nowy region formularza programu **Outlook)** stosuje atrybuty do klasy regionu formularza zawierającej określone nazwy klas komunikatów. Te atrybuty można również zastosować ręcznie.

### <a name="apply-class-attributes"></a>Stosowanie atrybutów klasy
 Po zakończeniu pracy kreatora Nowy region formularza programu Outlook możesz skojarzyć region formularza z klasą komunikatów **programu Outlook.** W tym celu należy zastosować atrybuty do klasy fabryki regionów formularza.

 W poniższym przykładzie przedstawiono <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> dwa atrybuty, które zostały zastosowane do klasy fabryki regionu formularza o nazwie `myFormRegion` . Pierwszy atrybut kojarzy region formularza ze standardową klasą wiadomości dla formularza wiadomości e-mail. Drugi atrybut kojarzy region formularza z niestandardową klasą komunikatów o nazwie `IPM.Task.Contoso` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs" id="Snippet1":::

 Atrybuty muszą być zgodne z następującymi wytycznymi:

- W przypadku niestandardowych klas komunikatów użyj w pełni kwalifikowanej nazwy klasy komunikatów (na przykład: "IPM. Note.Contoso").

- Nie określaj samej klasy komunikatów podstawowych (na przykład "IPM").

- Nie należy przekraczać 256 znaków dla każdej nazwy klasy komunikatów.

- Nie dołączaj nazw standardowych klas komunikatów, jeśli region formularza zastępuje cały formularz lub domyślną stronę formularza. Standardowe nazwy klas komunikatów można określić tylko dla formularzy, które dodają nową stronę do formularza lub które są dołączane do dołu formularza. Aby uzyskać więcej informacji, [zobacz How to: Add a form region to an Outlook Add-in project](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)(Jak dodać region formularza do projektu dodatku programu Outlook).

  Visual Studio weryfikuje format nazw klas komunikatów podczas kompilowania projektu.

> [!NOTE]
> Visual Studio sprawdza, czy nazwy klas komunikatów, które należy podać, są poprawne lub prawidłowe.

## <a name="see-also"></a>Zobacz też
- [Uzyskiwanie dostępu do regionu formularza w czasie uruchamiania](../vsto/accessing-a-form-region-at-run-time.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Przewodnik: projektowanie regionu formularza programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Wskazówki dotyczące tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Nazwa formularza i klasa komunikatów — omówienie](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)
- [Jak współpracują ze sobą formularze i elementy programu Outlook](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)
