---
title: Dostosowywanie wstążki dla programu Outlook
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 646192baa6caaa33410b1dd8d17d1983f7d27e30
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255550"
---
# <a name="customize-a-ribbon-for-outlook"></a>Dostosowywanie wstążki dla programu Outlook
  Po dostosowaniu wstążki w Microsoft Office Outlook należy rozważyć, gdzie wstążka niestandardowa będzie wyświetlana w aplikacji. W programie Outlook wstążka jest wyświetlana w głównym interfejsie użytkownika aplikacji oraz w oknach, które są otwierane, gdy użytkownicy wykonują określone zadania, takie jak tworzenie wiadomości e-mail. Te okna aplikacji są nazwanymi inspektorami.

 ![link do wideo](../vsto/media/playvideo.gif "link do wideo") Aby zapoznać się z pokrewną [prezentacją wideo, zobacz Jak mogę: Korzystanie z projektanta wstążki w celu dostosowania wstążki w programie Outlook? ](http://go.microsoft.com/fwlink/?LinkID=130312).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>Dodaj niestandardową Wstążkę do interfejsu użytkownika aplikacji głównej
 Interfejs użytkownika aplikacji głównej w programie Outlook nazywa się Eksploratorem. Jeśli używasz **wstążki (projektant graficzny)** , możesz dodać Wstążkę do Eksploratora, klikając Właściwość **wstążktype** wstążki w oknie **Właściwości** , a następnie wybierając pozycję **Microsoft. Outlook. Explorer**.

## <a name="assign-a-ribbon-to-an-inspector"></a>Przypisywanie wstążki do Inspektora
 Można zidentyfikować inspektora, który ma zostać dostosowany przez określenie typu wstążki, który odpowiada klasie komunikatów dla inspektora.

 Jeśli używasz **wstążki (projektant graficzny)** , kliknij właściwość **wstążka** wstążki w oknie **Właściwości** , a następnie wybierz co najmniej jeden identyfikator wstążki z listy wartości.

 Do projektu można dodać więcej niż jedną Wstążkę. Jeśli więcej niż jedna wstążka ma identyfikator wstążki, Zastąp `CreateRibbonExtensibilityObject` metodę `ThisAddin` w klasie projektu, aby określić, która wstążka ma być wyświetlana w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Omówienie wstążki](../vsto/ribbon-overview.md). Aby uzyskać więcej informacji na temat poszczególnych typów wstążki, zobacz artykuł techniczny [Dostosowywanie wstążki w programie Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Określ typ wstążki przy użyciu kodu XML wstążki
 Jeśli używasz elementu **wstążki (XML)** , sprawdź wartość <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> parametru *ribbonID* w metodzie i zwróć odpowiednią Wstążkę.

 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> Metoda jest generowana automatycznie przez program Visual Studio w pliku kodu wstążki. Parametr *ribbonID* jest ciągiem, który identyfikuje Eksploratora lub określony typ inspektora. Pełną listę możliwych wartości parametru *ribbonID* można znaleźć w artykule technicznym dotyczącym [dostosowywania wstążki w programie Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).

 Poniższy przykład kodu demonstruje, jak wyświetlić Wstążkę niestandardową tylko w `Microsoft.Outlook.Mail.Compose` Inspektorze. Jest to Inspektor otwierający się, gdy użytkownik tworzy nową wiadomość e-mail. Wstążka do wyświetlenia jest określona w `GetResourceText()` metodzie, która jest generowana w klasie **wstążki** . Aby uzyskać więcej informacji na temat klasy **wstążki** , zobacz [kod XML wstążki](../vsto/ribbon-xml.md).

 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]

## <a name="see-also"></a>Zobacz także
- [Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [XML — wstążka](../vsto/ribbon-xml.md)
