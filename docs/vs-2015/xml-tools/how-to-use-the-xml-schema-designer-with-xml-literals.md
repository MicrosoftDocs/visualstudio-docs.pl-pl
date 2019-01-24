---
title: 'Instrukcje: Używanie projektanta schematu XML z literałami XML | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 630505b317d5d8671a8214701cd2af13bfa40482
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54794716"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Instrukcje: Używanie projektanta schematu XML z literałami XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
W tym temacie opisano sposób wyświetlania schemat jest skojarzony z danymi XML literału w projekcie Visual Basic.  
  
### <a name="to-create-a-new-visual-basic-console-application-project"></a>Aby utworzyć nowy projekt aplikacji konsoli Visual Basic  
  
1.  Start Visual Studio 2010.  
  
2.  Z **pliku** menu, wybierz opcję **New**, a następnie wybierz pozycję **projektu**. **Nowy projekt** pojawi się okno dialogowe. Aby uzyskać **typów projektów**, wybierz opcję **inne języki** , a następnie wybierz **języka Visual Basic**. Aby uzyskać **szablony**, wybierz aplikację konsoli. Następnie wpisz `XMLLiterals` w **nazwa** pola i lokalizację projektu w **lokalizacji** pola. Kliknij przycisk **OK**.  
  
     Zostanie utworzony nowy projektu zlecenie serwisowe. Projekt XMLLiterals zawiera jeden plik źródłowy języka Visual Basic, Module1.vb.  
  
### <a name="to-add-an-existing-xsd-file-to-the-project"></a>Aby dodać istniejący plik XSD do projektu  
  
1.  Otwórz nowy tekst w pliku Notepad.Copy schematu XML przykładowego kodu z [schemat zamówienia zakupu](../xml-tools/sample-xsd-file-simple-schema.md) a następnie wklej je do pliku.  
  
2.  Zapisz plik w lokalizacji o nazwie PurchaseOrderSchema.xsd.  
  
3.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy nazwę projektu, wybierz **Dodaj**, a następnie wybierz pozycję **istniejący element...** . **Elementu AddExisting** pojawi się okno dialogowe. Przejdź do pliku PurchaseOrderSchema.xsd, zaznacz go, a następnie kliknij **Dodaj**.  
  
     Projekt XMLLiterals zawiera teraz dwa pliki: Module1.VB i PurchaseOrderSchema.xsd.  
  
### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Aby dodać kod języka Visual Basic z literał, XML na podstawie pliku XSD, zawarty w projekcie  
  
1.  Zastąp kod w pliku Module1.vb następującym kodem:  
  
    ```  
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
  
2.  Kliknij prawym przyciskiem myszy dowolny węzeł XML w literał XML lub importu przestrzeni nazw XML, a następnie wybierz pozycję **Pokaż w Eksploratorze schematu**.  
  
     Eksplorator schematu XML jest wyświetlany obok pliku Visual Basic, który ma literał assotiated ze schematem XML XML zestawu.
