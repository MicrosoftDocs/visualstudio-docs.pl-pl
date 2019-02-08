---
title: 'Instrukcje: Używanie projektanta schematu XML z literałami XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: cc4da90db115e001f7f06ec2e7dd33d64ef20048
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55927285"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Instrukcje: Używanie projektanta schematu XML z literałami XML

W tym temacie opisano sposób wyświetlania schemat jest skojarzony z danymi XML literału w projekcie Visual Basic.

## <a name="to-create-a-new-visual-basic-console-application-project"></a>Aby utworzyć nowy projekt aplikacji konsoli Visual Basic

1.  Uruchom program Visual Studio.

2.  Z **pliku** menu, wybierz opcję **New**, a następnie wybierz pozycję **projektu**. **Nowy projekt** pojawi się okno dialogowe. Aby uzyskać **typów projektów**, wybierz opcję **inne języki** , a następnie wybierz **języka Visual Basic**. Aby uzyskać **szablony**, wybierz aplikację konsoli. Następnie wpisz `XMLLiterals` w **nazwa** pola i lokalizację projektu w **lokalizacji** pola. Kliknij przycisk **OK**.

     Zostanie utworzony nowy projektu zlecenie serwisowe. Projekt XMLLiterals zawiera jeden plik źródłowy języka Visual Basic, *Module1.vb*.

## <a name="to-add-an-existing-xsd-file-to-the-project"></a>Aby dodać istniejący plik XSD do projektu

1.  Otwórz nowy plik tekstowy w Notatniku. Skopiuj przykładowy kod XML schematu z [schemat zamówienia zakupu](../xml-tools/sample-xsd-file-simple-schema.md) a następnie wklej je do pliku.

2.  Zapisz plik w lokalizacji o nazwie *PurchaseOrderSchema.xsd*.

3.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, wybierz **Dodaj**, a następnie wybierz pozycję **istniejący element**. **Elementu AddExisting** pojawi się okno dialogowe. Przejdź do *PurchaseOrderSchema.xsd* plików, wybierz ją, a następnie kliknij **Dodaj**.

     Projekt XMLLiterals zawiera teraz dwa pliki: *Module1.VB* i *PurchaseOrderSchema.xsd*.

## <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Aby dodać kod języka Visual Basic z literał, XML na podstawie pliku XSD, zawarty w projekcie

1. Zastąp kod w *Module1.vb* pliku następującym kodem:

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

2. Kliknij prawym przyciskiem myszy dowolny węzeł XML w literał XML lub importu przestrzeni nazw XML, a następnie wybierz pozycję **Pokaż w Eksploratorze schematu**.

    **Eksploratora schematu XML** jest wyświetlany obok plik w języku Visual Basic, który ma literał XML skojarzony zestaw schematów XML.