---
title: 'Instrukcje: Przełączanie się między widokami i edytorem XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09ad752dc87ea322396d6e6513593d71a7554b98
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53936246"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>Instrukcje: Przełączać się między widokami i edytorem XML

W tym temacie przedstawiono sposób przełączać się między widokami projektanta schematu XML (XSD Designer) i edytorem XML. W tym przykładzie użyto [schemat zamówienia zakupu](../xml-tools/sample-xsd-file-simple-schema.md).

## <a name="to-switch-between-the-views-and-the-xml-editor"></a>Aby przełączać się między widokami i edytorem XML

1.  Aby tworzyć i edytować plik schematu XML, wykonaj kroki opisane w [jak: Tworzenie i edytowanie pliku schematu XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Aby przełączyć się do projektanta schematu XML w edytorze XML, kliknij prawym przyciskiem myszy w edytorze XML, a następnie wybierz **Projektant widoków**.

3.  Aby przełączyć się do widoku wykresu przy użyciu znaku wodnego, kliknij przycisk **przy użyciu widoku wykresu można zobaczyć relację między węzłami** link widoku startowego.

4.  Przeciągnij `USAddress` węzła z **Eksploratora schematu XML** na widoku wykresu. Kliknij prawym przyciskiem myszy `USAddress` węzeł w widoku wykresu i wybierz **Pokaż w widoku modelu zawartości** w menu kontekstowym.

     Widok modelu zawartości ze szczegółami dotyczącymi `USAddress` węzeł jest dostępny.

5.  Aby przełączyć się do widoku startowego z widoku modelu zawartości za pomocą paska narzędzi, kliknij przycisk **widoku Start** na listwie narzędziowej XSD.

6.  Aby przełączyć się między widokami przy użyciu klawiszy dostępu, naciśnij klawisz **Ctrl**+**1** dla widoku startowego **Ctrl**+**2** dla widoku wykresu i **Ctrl**+**3** dla widoku modelu zawartości.

7.  Aby przejść do edytora XML z widoku modelu zawartości, kliknij prawym przyciskiem myszy węzeł, a następnie wybierz **Wyświetl kod** w menu kontekstowym.