---
title: Dostosowywanie wstążki dla programu InfoPath
description: Dowiedz się, że po dostosowaniu wstążki w Microsoft Office InfoPath należy rozważyć, gdzie wstążka niestandardowa będzie wyświetlana w aplikacji.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: baf5a7edbdd9452c4b7ce55e109eee9c79798b5e
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844170"
---
# <a name="customize-a-ribbon-for-infopath"></a>Dostosowywanie wstążki dla programu InfoPath
  Po dostosowaniu wstążki w Microsoft Office InfoPath należy rozważyć, gdzie wstążka niestandardowa będzie wyświetlana w aplikacji. [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] można wyświetlić Wstążkę w następujących trzech typach okien aplikacji programu InfoPath:

- System Windows, który wyświetla szablon formularza otwarty w trybie projektowania.

- System Windows, który wyświetla formularz oparty na szablonie formularza.

- Okno podglądu wydruku.

  **Dotyczy:** Informacje przedstawione w tym temacie dotyczą projektów dodatku VSTO dla programu InfoPath 2010. Aby uzyskać więcej informacji, zobacz [dostępność funkcji według aplikacji pakietu Office i typów projektów](../vsto/features-available-by-office-application-and-project-type.md).

  Użytkownicy i projektanci otwierają szablon formularza w trybie projektowania, aby modyfikować wygląd i układ szablonu. Użytkownicy otwierają formularze, które są oparte na szablonie formularza do dodawania zawartości.

  Okno podglądu wydruku umożliwia projektantom i użytkownikom wyświetlanie podglądu stron formularza lub szablonu formularza przed ich wydrukowaniem.

> [!NOTE]
> Karta **Dodatki** nie jest wyświetlana w oknie Podgląd wydruku. Jeśli chcesz, aby w oknie podglądu wydruku była wyświetlana karta niestandardowa, upewnij się, że właściwość **OfficeId** karty nie jest ustawiona na **TabAddIns**.

 Należy określić typ wstążki dla każdego okna, w którym ma zostać wyświetlona wstążka.

## <a name="specify-the-ribbon-type-in-the-ribbon-designer"></a>Określanie typu wstążki w Projektancie wstążki
 Jeśli używasz **wstążki (projektant graficzny)** , kliknij właściwość **wstążka** wstążki w oknie **Właściwości** , a następnie wybierz dowolne identyfikatory wstążki opisane w poniższej tabeli.

|Identyfikator wstążki|Okno, w którym wstążka będzie wyświetlana podczas uruchamiania projektu|
|---------------|---------------------------------------------------------------------|
|**Microsoft. InfoPath. Designer**|System Windows, który wyświetla szablon formularza otwarty w trybie projektowania.|
|**Microsoft. InfoPath. Editor**|System Windows, który wyświetla formularz oparty na szablonie formularza.|
|**Microsoft. InfoPath. PrintPreview**|Okno podglądu wydruku.|

 Do projektu można dodać więcej niż jedną Wstążkę. Jeśli więcej niż jedna wstążka korzysta z identyfikatora wstążki, Zastąp `CreateRibbonExtensibilityObject` metodę w `ThisAddin` klasie projektu, aby określić, która wstążka ma być wyświetlana w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Omówienie wstążki](../vsto/ribbon-overview.md).

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Określ typ wstążki przy użyciu kodu XML wstążki
 Jeśli używasz elementu **wstążki (XML)** , sprawdź wartość parametru *ribbonID* w <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> metodzie i zwróć odpowiednią Wstążkę.

 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A>Metoda jest generowana automatycznie przez program Visual Studio w pliku kodu wstążki. Parametr *ribbonID* jest ciągiem, który identyfikuje typ okna programu InfoPath, które jest otwierane.

 Poniższy przykład kodu demonstruje, jak wyświetlić Wstążkę niestandardową tylko w oknie, w którym jest wyświetlany szablon formularza w trybie projektowania. Wstążka do wyświetlenia jest określona w `GetResourceText()` metodzie, która jest generowana w klasie wstążki. Aby uzyskać więcej informacji na temat klasy wstążki, zobacz [kod XML wstążki](../vsto/ribbon-xml.md).

 [!code-csharp[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs#1)]
 [!code-vb[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb#1)]

## <a name="see-also"></a>Zobacz także
- [Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)
- [Omówienie wstążki](../vsto/ribbon-overview.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [XML — Wstążka](../vsto/ribbon-xml.md)
