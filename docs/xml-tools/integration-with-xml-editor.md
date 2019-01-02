---
title: Projektant schematu XML integracji za pomocą edytora XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3a4d97ce590929b6cc2cf56997255822b692cc9e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865016"
---
# <a name="integration-with-xml-editor"></a>Integracja z edytorem XML

Projektant schematu XML jest zintegrowana za pomocą edytora XML. Jeśli zmodyfikujesz plik XSD w edytorze XML, zmiany zostaną odzwierciedlone w [Eksploratora schematu XML](../xml-tools/xml-schema-explorer.md). Jeśli masz [widoku wykresu](../xml-tools/graph-view.md) lub [widoku modelu zawartości](../xml-tools/content-model-view.md) otwarte, zmiany zostaną także odzwierciedlone istnieje. Możesz przechodzić między projektanta schematu XML i edytorem XML w następujący sposób:

-   W edytorze XML, kliknij prawym przyciskiem myszy węzeł i wybierz **Pokaż w Eksplorator schematu XML**.

-   W widoku wykresu i **Eksploratora schematu XML**, kliknij dwukrotnie węzeł, lub kliknij prawym przyciskiem myszy węzeł i wybierz pozycję **Wyświetl kod**. W widoku modelu zawartości, kliknij prawym przyciskiem myszy węzeł, a następnie wybierz **Wyświetl kod**.

Poniższy zrzut ekranu przedstawia schematu XML, który jest otwierany w **Eksploratora schematu XML**. **Eksploratora schematu XML** Wyświetla schemat w widoku drzewa. Edytor XML przedstawia widok tekstu węzła, który jest aktualnie aktywne w **Eksploratora schematu XML**.

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

Czasami warto wyświetlić kod w edytorze XML i graficzny Projektant obok siebie. Aby wyświetlić oba pliki, w tym samym czasie, kliknij prawym przyciskiem myszy w edytorze XML, a następnie wybierz **Projektant widoków**. Wybierz z menu programu Visual Studio Windows **nowe poziomy (lub w pionie) grupy kart**.

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Zobacz także

- [Eksplorator schematu XML](../xml-tools/xml-schema-explorer.md)