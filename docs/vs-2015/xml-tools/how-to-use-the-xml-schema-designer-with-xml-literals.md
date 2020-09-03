---
title: 'Instrukcje: korzystanie z projektanta schematu XML z literałami XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a9e82cf8387756cb4a4abe8b4c41d082485cdcdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656294"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Instrukcje: Używanie projektanta schematu XML z literałami XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano sposób wyświetlania schematu skojarzonego z literałem XML w projekcie Visual Basic.

### <a name="to-create-a-new-visual-basic-console-application-project"></a>Aby utworzyć nowy projekt aplikacji konsolowej Visual Basic

1. Uruchom program Visual Studio 2010.

2. Z menu **plik** wybierz pozycję **Nowy**, a następnie wybierz pozycję **projekt**. Zostanie wyświetlone okno dialogowe **Nowy projekt**. W obszarze **typy projektów**wybierz pozycję **inne języki,** a następnie wybierz pozycję **Visual Basic**. W obszarze **Szablony**wybierz pozycję Aplikacja konsolowa. Następnie wpisz `XMLLiterals` w polu **Nazwa** i lokalizację projektu w polu **Lokalizacja** . Kliknij przycisk **OK**.

     Zostanie utworzony nowy poject. Projekt XMLLiterals zawiera jeden Visual Basic plik źródłowy, Module1. vb.

### <a name="to-add-an-existing-xsd-file-to-the-project"></a>Aby dodać istniejący plik XSD do projektu

1. Otwórz nowy plik tekstowy w Notatniku. Skopiuj przykładowy kod schematu XML z [schematu zamówienia zakupu](../xml-tools/sample-xsd-file-simple-schema.md) i wklej go do pliku.

2. Zapisz plik w lokalizacji o nazwie PurchaseOrderSchema. xsd.

3. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy nazwę projektu, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **istniejący element.**... Zostanie wyświetlone okno dialogowe **AddExisting Item** . Przejdź do pliku PurchaseOrderSchema. xsd, zaznacz go, a następnie kliknij przycisk **Dodaj**.

     Projekt XMLLiterals zawiera teraz dwa pliki: Module1. vb i PurchaseOrderSchema. xsd.

### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Aby dodać kod Visual Basic za pomocą literału XML, na podstawie pliku XSD zawartego w projekcie

1. Zastąp kod w pliku Module1. vb następującym kodem:

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

2. Kliknij prawym przyciskiem myszy dowolny węzeł XML w literale XML lub Importuj przestrzeń nazw XML i wybierz **Pokaż w Eksploratorze schematu**.

     Eksplorator schematu XML jest wyświetlany obok pliku Visual Basic, który ma literał XML assotiated z zestawem schematu XML.
