---
title: Dostosowywanie wstążki dla programu Outlook
description: Dowiedz się, że podczas dostosowywania wstążki w programie Microsoft Office Outlook należy rozważyć miejsce, w którym wstążka niestandardowa będzie wyświetlana w aplikacji.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: df28de0f8a9497fabecff816c26db7593bf349bd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828062"
---
# <a name="customize-a-ribbon-for-outlook"></a>Dostosowywanie wstążki dla programu Outlook
  Podczas dostosowywania wstążki w programie Microsoft Office Outlook należy rozważyć miejsce, w którym wstążka niestandardowa będzie wyświetlana w aplikacji. Program Outlook wyświetla wstążkę w głównym interfejsie użytkownika aplikacji i w oknach otwieranych, gdy użytkownicy wykonują pewne zadania, takie jak tworzenie wiadomości e-mail. Te okna aplikacji są nazywane inspektorami.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>Dodawanie niestandardowej wstążki do głównego interfejsu użytkownika aplikacji
 Główny interfejs użytkownika aplikacji w programie Outlook jest nazywany Eksploratorem. Jeśli używasz elementu Wstążki **(Projektant** wizualny), możesz dodać wstążkę do Eksploratora, klikając właściwość  **RibbonType** wstążki w oknie Właściwości, a następnie wybierając pozycję **Microsoft.Outlook.Explorer.**

## <a name="assign-a-ribbon-to-an-inspector"></a>Przypisywanie wstążki do inspektora
 Aby zidentyfikować inspektora, który chcesz dostosować, określ typ wstążki odpowiadający klasie komunikatów dla inspektora.

 Jeśli używasz elementu Wstążki **(Projektant** wizualny), kliknij właściwość **RibbonType** wstążki  w oknie Właściwości, a następnie wybierz z listy wartości co najmniej jeden identyfikator wstążki.

 Do projektu można dodać więcej niż jedną wstążkę. Jeśli więcej niż jedna wstążka ma identyfikator wstążki, zastąp metodę w klasie projektu, aby określić, która wstążka ma być `CreateRibbonExtensibilityObject` `ThisAddin` wyświetlana w czasie uruchamiania. Aby uzyskać więcej informacji, zobacz [Omówienie wstążki.](../vsto/ribbon-overview.md) Aby uzyskać więcej informacji na temat poszczególnych typów wstążki, zobacz artykuł techniczny Dostosowywanie wstążki w [programie Outlook 2007.](/previous-versions/office/developer/office-2007/bb226712(v=office.12))

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Określanie typu wstążki przy użyciu xml wstążki
 Jeśli używasz elementu **Wstążki (XML),** sprawdź wartość parametru *ribbonID* w metodzie i <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> zwróć odpowiednią wstążkę.

 Metoda <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> jest generowana automatycznie przez Visual Studio w pliku kodu wstążki. Parametr *ribbonID* to ciąg, który identyfikuje Eksploratora lub określony typ inspektora. Pełną listę możliwych wartości parametru *ribbonID* można znaleźć w artykule technicznym Customize the Ribbon in Outlook 2007 (Dostosowywanie wstążki w [programie Outlook 2007).](/previous-versions/office/developer/office-2007/bb226712(v=office.12))

 Poniższy przykład kodu pokazuje, jak wyświetlić niestandardową wstążkę tylko w `Microsoft.Outlook.Mail.Compose` inspektorze. Jest to inspektor, który jest otwierany, gdy użytkownik tworzy nową wiadomość e-mail. Wstążka do wyświetlenia jest określona w `GetResourceText()` metodzie , która jest generowana w klasie **Wstążki.** Aby uzyskać więcej informacji na temat klasy **wstążki,** zobacz [Xml wstążki](../vsto/ribbon-xml.md).

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb" id="Snippet1":::

## <a name="see-also"></a>Zobacz też
- [Uzyskiwanie dostępu do wstążki w czasie uruchamiania](../vsto/accessing-the-ribbon-at-run-time.md)
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [XML — Wstążka](../vsto/ribbon-xml.md)
