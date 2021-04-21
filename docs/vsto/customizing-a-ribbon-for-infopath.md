---
title: Dostosowywanie wstążki dla programu InfoPath
description: Dowiedz się, że podczas dostosowywania wstążki w programie Microsoft Office InfoPath należy rozważyć miejsce, w którym niestandardowa wstążka będzie wyświetlana w aplikacji.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- InfoPath [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], InfoPath
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5af7c4ed2f396c5a806cc42c49c8f4209b6b5c2c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828140"
---
# <a name="customize-a-ribbon-for-infopath"></a>Dostosowywanie wstążki dla programu InfoPath
  Podczas dostosowywania wstążki w programie Microsoft Office InfoPath należy rozważyć miejsce, w którym niestandardowa wstążka będzie wyświetlana w aplikacji. [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] Może wyświetlać wstążkę w następujących trzech typach okien aplikacji InfoPath:

- W systemie Windows jest wyświetlany szablon formularza, który jest otwierany w trybie projektowania.

- W systemie Windows wyświetlany jest formularz oparty na szablonie formularza.

- Okno Podgląd wydruku.

  **Dotyczy:** Informacje zawarte w tym temacie dotyczą projektów dodatków VSTO dla programu InfoPath 2010. Aby uzyskać więcej informacji, zobacz [Funkcje dostępne według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

  Użytkownicy i projektanci otwierają szablon formularza w trybie projektowania, aby zmodyfikować wygląd i układ szablonu. Użytkownicy otwierają formularze oparte na szablonie formularza w celu dodania zawartości.

  Okno Podgląd wydruku umożliwia projektantom i użytkownikom wyświetlanie podglądu stron formularza lub szablonu formularza przed ich wydrukowaniem.

> [!NOTE]
> Karta **AddIns** nie jest wyświetlana w oknie Podgląd wydruku. Jeśli chcesz, aby karta niestandardowa była wyświetlana w oknie Podgląd wydruku, upewnij się, że właściwość **OfficeId** karty nie jest ustawiona na wartość **TabAddIns.**

 Należy określić typ wstążki każdego okna, w którym ma być wyświetlana wstążka.

## <a name="specify-the-ribbon-type-in-the-ribbon-designer"></a>Określanie typu wstążki w projektancie wstążki
 Jeśli używasz elementu **Wstążka (Projektant** wizualny), kliknij właściwość **RibbonType**  wstążki w oknie Właściwości, a następnie wybierz dowolny identyfikator wstążki opisany w poniższej tabeli.

|Identyfikator wstążki|Okno, w którym wstążka pojawi się po uruchomieniu projektu|
|---------------|---------------------------------------------------------------------|
|**Microsoft.InfoPath.Designer**|W systemie Windows jest wyświetlany szablon formularza, który jest otwierany w trybie projektowania.|
|**Microsoft.InfoPath.Editor**|Okna, w których jest wyświetlany formularz oparty na szablonie formularza.|
|**Microsoft.InfoPath.PrintPreview**|Okno Podgląd wydruku.|

 Do projektu można dodać więcej niż jedną wstążkę. Jeśli więcej niż jedna wstążka ma współużytkować identyfikator wstążki, zastąp metodę w klasie projektu, aby określić, która wstążka ma być `CreateRibbonExtensibilityObject` `ThisAddin` wyświetlana w czasie uruchamiania. Aby uzyskać więcej informacji, zobacz [Omówienie wstążki](../vsto/ribbon-overview.md).

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Określanie typu wstążki przy użyciu xml wstążki
 Jeśli używasz elementu **Wstążki (XML),** sprawdź wartość parametru *ribbonID* w metodzie i <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> zwróć odpowiednią wstążkę.

 Metoda <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> jest generowana automatycznie przez Visual Studio w pliku kodu wstążki. Parametr *ribbonID* to ciąg, który identyfikuje typ otwieranych okien InfoPath.

 Poniższy przykład kodu pokazuje, jak wyświetlić niestandardową wstążkę tylko w oknie, które wyświetla szablon formularza w trybie projektowania. Wstążka do wyświetlenia jest określona `GetResourceText()` w metodzie , która jest generowana w klasie Wstążki. Aby uzyskać więcej informacji na temat klasy wstążki, zobacz [Xml wstążki](../vsto/ribbon-xml.md).

 :::code language="csharp" source="../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb" id="Snippet1":::

## <a name="see-also"></a>Zobacz też
- [Uzyskiwanie dostępu do wstążki w czasie uruchamiania](../vsto/accessing-the-ribbon-at-run-time.md)
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [XML — Wstążka](../vsto/ribbon-xml.md)
