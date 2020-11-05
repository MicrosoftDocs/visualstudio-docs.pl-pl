---
title: 'Instrukcje: przełączanie się między widokami a edytorem XML'
description: Dowiedz się, jak przełączać się między widokami projektanta schematu XML (XSD Designer) a edytorem XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef64617591da0790a26e4728cd138d2224deed8e
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400131"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>Instrukcje: przełączanie się między widokami a edytorem XML

W tym temacie pokazano, jak przełączać się między widokami projektanta schematu XML (XSD Designer) a edytorem XML. W tym przykładzie zastosowano [schemat zamówienia zakupu](../xml-tools/sample-xsd-file-simple-schema.md).

## <a name="to-switch-between-the-views-and-the-xml-editor"></a>Aby przełączać się między widokami i edytorem XML

1. Aby utworzyć i edytować nowy plik schematu XML, wykonaj kroki opisane w temacie [How to: Create and Edit a XSD File Schema](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Aby przełączyć się do projektanta schematu XML z edytora XML, kliknij prawym przyciskiem myszy w dowolnym miejscu w edytorze XML i wybierz polecenie **Projektant widoków**.

3. Aby przełączyć się do widoku wykresu przy użyciu znaku wodnego, kliknij przycisk **Użyj widoku wykresu, aby zobaczyć relację między węzłem węzły** w widoku Start.

4. Przeciągnij `USAddress` węzeł z **Eksploratora schematu XML** na widok wykresu. Kliknij prawym przyciskiem myszy `USAddress` węzeł w widoku wykresu i wybierz polecenie **Pokaż w widoku modelu zawartości** w menu kontekstowym.

     Zostanie wyświetlony widok model zawartości z szczegółowymi informacjami o `USAddress` węźle.

5. Aby przełączyć się do widoku Start z widoku modelu zawartości przy użyciu paska narzędzi, kliknij przycisk **Wyświetl widok** na pasku narzędzi XSD.

6. Aby przełączać się między widokami za pomocą klawiszy skrótów, naciśnij **Ctrl** + **1** dla widoku Start, **Ctrl** + **2** dla widoku wykresu i **Ctrl** + **3** dla widoku modelu zawartości.

7. Aby przejść do edytora XML z widoku modelu zawartości, kliknij prawym przyciskiem myszy węzeł i wybierz polecenie **Wyświetl kod** w menu kontekstowym.
