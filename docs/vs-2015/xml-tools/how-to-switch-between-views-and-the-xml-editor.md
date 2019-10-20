---
title: 'Instrukcje: przełączanie się między widokami a edytorem XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 28267f705dd9a747d0e3f3ac5dc2869ab7de8f6a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656316"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>Instrukcje: przełączanie się między widokami a edytorem XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie pokazano, jak przełączać się między widokami projektanta schematu XML (XSD Designer) a edytorem XML. W tym przykładzie zastosowano [schemat zamówienia zakupu](../xml-tools/sample-xsd-file-simple-schema.md).

### <a name="to-switch-between-the-views-and-the-xml-editor"></a>Aby przełączać się między widokami i edytorem XML

1. Aby utworzyć i edytować nowy plik schematu XML, wykonaj kroki opisane w temacie [How to: Create and Edit a XSD File Schema](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Aby przełączyć się do projektanta schematu XML z edytora XML, kliknij prawym przyciskiem myszy w dowolnym miejscu w edytorze XML i wybierz polecenie **Projektant widoków**.

3. Aby przełączyć się do widoku wykresu przy użyciu znaku wodnego, kliknij przycisk **Użyj widoku wykresu, aby zobaczyć relację między węzłem węzły** w widoku Start.

4. Przeciągnij węzeł `USAddress` z Eksploratora schematu XML na widok wykresu. Kliknij prawym przyciskiem myszy węzeł `USAddress` w widoku wykresu i wybierz polecenie **Pokaż w widoku modelu zawartości** w menu kontekstowym.

     Zostanie wyświetlony widok model zawartości z szczegółowymi węzłami `USAddress`.

5. Aby przełączyć się do widoku Start z widoku modelu zawartości przy użyciu paska narzędzi, kliknij przycisk Wyświetl widok na pasku narzędzi XSD.

6. Aby przełączać się między widokami za pomocą klawiszy skrótów, naciśnij kombinację klawiszy CTRL + 1 dla widoku Start, CTRL + 2 dla widoku wykresu i CTRL + 3 dla widoku modelu zawartości.

7. Aby przejść do edytora XML z widoku modelu zawartości, kliknij prawym przyciskiem myszy węzeł i wybierz polecenie **Wyświetl kod** w menu kontekstowym.
