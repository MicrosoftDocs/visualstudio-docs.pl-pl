---
title: Integracja projektanta schematu XML z edytorem XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9df2d97a6ff68299ab70545683970188eb1bfea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601782"
---
# <a name="integration-with-xml-editor"></a>Integracja z edytorem XML

Projektant schematu XML jest zintegrowany z edytorem XML. Jeśli zmodyfikujesz plik XSD w edytorze XML, zmiana zostanie odzwierciedlona w [Eksploratorze schematu XML](../xml-tools/xml-schema-explorer.md). Jeśli masz [Widok wykresu](../xml-tools/graph-view.md) lub otwarty [Widok modelu zawartości](../xml-tools/content-model-view.md) , zmiana zostanie również odzwierciedlona. Możesz nawigować między projektantem schematu XML a edytorem XML w następujący sposób:

- W edytorze XML kliknij prawym przyciskiem myszy węzeł i wybierz polecenie **Pokaż w Eksploratorze schematu XML**.

- W widoku wykresu i w **Eksploratorze schematu XML**, kliknij dwukrotnie węzeł, lub kliknij prawym przyciskiem myszy węzeł i wybierz polecenie **Wyświetl kod**. W widoku model zawartości kliknij prawym przyciskiem myszy węzeł i wybierz polecenie **Wyświetl kod**.

Poniższy zrzut ekranu przedstawia schemat XML otwarty w **Eksploratorze schematu XML**. **Eksplorator schematu XML** Wyświetla zestaw schematów w widoku drzewa. Edytor XML Wyświetla widok tekstu węzła, który jest obecnie aktywny w **Eksploratorze schematu XML**.

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

Czasami warto zobaczyć kod w edytorze XML i projektanta graficznego obok siebie. Aby wyświetlić oba pliki w tym samym czasie, kliknij prawym przyciskiem myszy w dowolnym miejscu w edytorze XML i wybierz polecenie **Projektant widoków**. W menu programu Visual Studio systemu Windows wybierz kolejno pozycje **Nowa pozioma (lub pionowa) Grupa kart**.

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Zobacz także

- [Eksplorator schematu XML](../xml-tools/xml-schema-explorer.md)