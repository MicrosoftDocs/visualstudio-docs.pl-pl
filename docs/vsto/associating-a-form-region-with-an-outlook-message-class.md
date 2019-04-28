---
title: Kojarzenie regionu formularza z klasą wiadomości programu Outlook
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5c264048887d3a1ba77d498784dc3e6cc4384159
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440361"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Kojarzenie regionu formularza z klasą wiadomości programu Outlook
  Można określić elementy, które program Microsoft Office Outlook wyświetlania regionu formularza przez kojarzenie regionu formularza z klasą wiadomości dla każdego elementu. Na przykład, jeśli chcesz dołączyć regionu formularza do dolnej części elementu poczty, można skojarzyć regionu formularza z `IPM.Note` klasą wiadomości.

 Aby skojarzyć regionu formularza z klasą wiadomości, określ nazwę klasy wiadomości w **nowy Region formularza programu Outlook** kreatora lub zastosować atrybut do klasy fabryka regionów formularza.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="understand-outlook-message-classes"></a>Omówienie klas wiadomości programu Outlook
 Klasą wiadomości programu Outlook identyfikuje typ elementu programu Outlook. W poniższej tabeli wymieniono te osiem standardowe typy elementów i ich nazwy klas wiadomości.

|Typ elementu programu Outlook|Nazwa klasy wiadomości|
|-----------------------|------------------------|
|AppointmentItem|`IPM.Appointment`|
|ContactItem|`IPM.Contact`|
|DistListItem|`IPM.DistList`|
|JournalItem|`IPM.Activity`|
|MailItem|`IPM.Note`|
|PostItem|`IPM.Post` lub `IPM.Post.RSS`|
|TaskItem|`IPM.Task`|

 Można również określić nazwy niestandardowych klasach wiadomości. Niestandardowych klasach wiadomości zidentyfikować niestandardowych formularzy utworzonych w programie Outlook.

> [!NOTE]
> Zastąpienie i regionów formularza Zamień wszystkie można określić nową nazwę klasy niestandardowy komunikat. Nie trzeba użyć nazwy klas wiadomości istniejącego formularza niestandardowego. Nazwa niestandardowej klasy wiadomości musi być unikatowa. Jednym ze sposobów, aby upewnić się, że nazwa jest unikatowa jest do Konwencja nazewnictwa podobny do następującego: \<*StandardMessageClassName*>.\< *Firmy*>.\< *MessageClassName*> (na przykład: `IPM.Note.Contoso.MyMessageClass`).

## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Kojarzenie regionu formularza z klasą wiadomości programu Outlook
 Istnieją dwa sposoby kojarzenie regionu formularza z klasą wiadomości:

- Użyj **nowy Region formularza programu Outlook** kreatora.

- Zastosuj atrybuty klasy.

### <a name="use-the-new-outlook-form-region-wizard"></a>Za pomocą Kreatora nowego regionu formularza programu Outlook
 Na ostatniej stronie **nowy Region formularza programu Outlook** kreatora można wybrać standardowych klasach wiadomości i wpisz nazwy niestandardowych klasach wiadomości, które chcesz skojarzyć z regionu formularza.

 Standardowych klasach wiadomości nie są dostępne, gdy region formularza zaprojektowano w celu zastąpienia cały formularz lub domyślną stronę formularza. Można określić nazwy klas standardową wiadomość tylko w przypadku formularzy, Dodaj nową stronę do formularza lub które są dołączane do dolnej części formularza. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

 Aby dołączyć co najmniej jedną klasę niestandardowy komunikat, wpisz ich nazwy w **których niestandardowych klasach wiadomości będzie wyświetlany ten region formularza?** pole.

 Nazwy, które podczas pisania muszą przestrzegać następujących wytycznych:

- Użyj wiadomości w pełni kwalifikowaną nazwę klasy (na przykład: "IPM.Note.Contoso").

- Użyj średników do oddzielenia nazwy klas wiadomości.

- Nie należy dołączać standardowych klas wiadomości programu Outlook, takich jak "IPM. Note"lub"IPM. Skontaktuj się z". Uwzględnij tylko niestandardowych klasach wiadomości, takich jak "IPM. Note.Contoso".

- Nie określono klasy bazowej wiadomości samodzielnie (na przykład: "IPM").

- Nie może przekraczać 256 znaków dla każdej nazwy klas wiadomości.

  **Nowy Region formularza programu Outlook** Kreator sprawdza poprawność format dane wejściowe, po kliknięciu **Zakończ**.

> [!NOTE]
> **Nowy Region formularza programu Outlook** Kreator sprawdza, czy nazwy klas wiadomości, które należy podać są poprawne lub jest nieprawidłowy.

 Po zakończeniu działania kreatora **nowy Region formularza programu Outlook** Kreator ma zastosowanie atrybutów do klasy regionu formularza, która zawiera nazwy klas określony komunikat. Można także ręcznie zastosować te atrybuty.

### <a name="apply-class-attributes"></a>Zastosuj atrybuty klasy
 Możesz skojarzyć regionu formularza z klasą wiadomości programu Outlook, po ukończeniu **nowy Region formularza programu Outlook** kreatora. Aby to zrobić, należy zastosować atrybutów do klasy fabryka regionów formularza.

 W poniższym przykładzie pokazano dwa <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> atrybuty, które zostały zastosowane do klasy fabryka regionów formularza o nazwie `myFormRegion`. Pierwszy atrybut kojarzy regionu formularza z klasą standardową wiadomość dla formularza wiadomość poczty. Drugi atrybut kojarzy regionu formularza z niestandardową klasę wiadomości o nazwie `IPM.Task.Contoso`.

 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]

 Atrybuty muszą być zgodne z następującymi wytycznymi:

- Dla niestandardowych klasach wiadomości, użyj wiadomości w pełni kwalifikowaną nazwę klasy (na przykład: "IPM.Note.Contoso").

- Nie określono klasy bazowej wiadomości samodzielnie (na przykład: "IPM").

- Nie może przekraczać 256 znaków dla każdej nazwy klas wiadomości.

- Nie należy dołączać nazwy standardowych klasach wiadomości, jeśli region formularza zastępuje cały formularz lub domyślną stronę formularza. Można określić nazwy klas standardową wiadomość tylko w przypadku formularzy, Dodaj nową stronę do formularza lub które są dołączane do dolnej części formularza. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

  Podczas kompilowania projektu programu Visual Studio sprawdza poprawność format nazwy klas wiadomości.

> [!NOTE]
> Program Visual Studio nie sprawdza, czy nazwy klas wiadomości, które należy podać prawidłowy lub jest nieprawidłowy.

## <a name="see-also"></a>Zobacz także
- [Dostęp do regionów formularzy w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Przewodnik: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Wytyczne dotyczące tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Nazwa formularza i komunikat klasy — omówienie](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)
- [Jak formularzy programu Outlook i elementy współpracują ze sobą](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)
