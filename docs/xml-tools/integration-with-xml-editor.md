---
title: Integracja projektanta schematu XML z edytorem XML
description: Dowiedz się więcej o integracji między projektantem schematu XML i edytorem XML oraz sposobie odzwierciedlania zmian wprowadzonych w jednym z nich.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9569e33f8f9f861bc5d89030c6fe38b0ab853a6f
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400190"
---
# <a name="integration-with-xml-editor"></a>Integracja z edytorem XML

Projektant schematu XML jest zintegrowany z edytorem XML. Jeśli zmodyfikujesz plik XSD w edytorze XML, zmiana zostanie odzwierciedlona w [Eksploratorze schematu XML](../xml-tools/xml-schema-explorer.md). Jeśli masz [Widok wykresu](../xml-tools/graph-view.md) lub otwarty [Widok modelu zawartości](../xml-tools/content-model-view.md) , zmiana zostanie również odzwierciedlona. Możesz nawigować między projektantem schematu XML a edytorem XML w następujący sposób:

- W edytorze XML kliknij prawym przyciskiem myszy węzeł i wybierz polecenie **Pokaż w Eksploratorze schematu XML**.

- W widoku wykresu i w **Eksploratorze schematu XML** , kliknij dwukrotnie węzeł, lub kliknij prawym przyciskiem myszy węzeł i wybierz polecenie **Wyświetl kod**. W widoku model zawartości kliknij prawym przyciskiem myszy węzeł i wybierz polecenie **Wyświetl kod**.

Poniższy zrzut ekranu przedstawia schemat XML otwarty w **Eksploratorze schematu XML**. **Eksplorator schematu XML** Wyświetla zestaw schematów w widoku drzewa. Edytor XML Wyświetla widok tekstu węzła, który jest obecnie aktywny w **Eksploratorze schematu XML**.

![Zrzut ekranu przedstawiający projekt programu Visual Studio, w którym znajduje się węzeł XML w okienku edytora XML i widok drzewa zestawu schematu w okienku Eksplorator schematu XML.](../xml-tools/media/xsddesignerwithxmleditor.gif)

Czasami warto zobaczyć kod w edytorze XML i projektanta graficznego obok siebie. Aby wyświetlić oba pliki w tym samym czasie, kliknij prawym przyciskiem myszy w dowolnym miejscu w edytorze XML i wybierz polecenie **Projektant widoków**. W menu programu Visual Studio systemu Windows wybierz kolejno pozycje **Nowa pozioma (lub pionowa) Grupa kart**.

![Zrzut ekranu przedstawiający projekt programu Visual Studio, który zawiera okienko widok projektanta, okienko edytora XML i okienko Eksplorator schematu XML.](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Zobacz też

- [Eksplorator schematu XML](../xml-tools/xml-schema-explorer.md)
