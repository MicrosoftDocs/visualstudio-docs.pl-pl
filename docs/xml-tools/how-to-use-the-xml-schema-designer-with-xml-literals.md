---
title: 'Instrukcje: Używanie projektanta schematu XML z literałami XML'
description: Dowiedz się, jak używać projektanta schematu XML do wyświetlania schematu skojarzonego z literałem XML w projekcie Visual Basic.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3b86cc50e5a25466b0ec80e45a225d64b8a97f72
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399175"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Instrukcje: korzystanie z projektanta schematu XML z literałami XML

W tym temacie opisano sposób wyświetlania schematu skojarzonego z literałem XML w projekcie Visual Basic.

## <a name="create-a-new-visual-basic-project"></a>Utwórz nowy projekt Visual Basic

1. Otwórz program Visual Studio.

2. Utwórz nowy projekt **aplikacji konsoli** Visual Basic o nazwie **XMLLiterals**.

     Nowy projekt zawiera jeden Visual Basic plik źródłowy, *Module1. vb*.

## <a name="add-an-existing-xsd-file"></a>Dodaj istniejący plik XSD

1. Otwórz nowy plik tekstowy w Notatniku. Skopiuj przykładowy kod schematu XML z [schematu zamówienia zakupu](../xml-tools/sample-xsd-file-simple-schema.md) i wklej go do pliku.

2. Zapisz plik w lokalizacji o nazwie *PurchaseOrderSchema. xsd*.

3. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy nazwę projektu, wybierz polecenie **Dodaj** , a następnie wybierz pozycję **istniejący element**. Zostanie wyświetlone okno dialogowe **AddExisting Item** . Przejdź do pliku *PurchaseOrderSchema. xsd* , zaznacz go, a następnie kliknij przycisk **Dodaj**.

     Projekt XMLLiterals zawiera teraz dwa pliki: *Module1. vb* i *PurchaseOrderSchema. xsd*.

## <a name="add-code"></a>Dodaj kod

Aby dodać kod Visual Basic za pomocą literału XML, na podstawie pliku XSD zawartego w projekcie:

1. Zastąp kod w pliku *Module1. vb* następującym kodem:

   ```vb
   Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">

   Module Module1
      Sub Main()

          Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">
                               <ns:ShipTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:ShipTo>
                               <ns:BillTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:BillTo>
                           </ns:PurchaseOrder>

      End Sub
   End Module
   ```

2. Kliknij prawym przyciskiem myszy dowolny węzeł XML w literale XML lub Importuj przestrzeń nazw XML i wybierz **Pokaż w Eksploratorze schematu**.

   **Eksplorator schematu XML** jest wyświetlany obok pliku Visual Basic, który ma literał XML skojarzony z zestawem schematu XML.
