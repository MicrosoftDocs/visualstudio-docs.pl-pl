---
title: 'Instrukcje: Udostępnianie kodu z VBA w projektach Visual Basic'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 12a5f19574974ce8d3928997a6b02bbf59062d89
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60101329"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>Instrukcje: Udostępnianie kodu z VBA w projektach Visual Basic
  Można udostępnić kod w [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projekt języka Visual Basic for Applications (VBA) kod Jeśli chcesz, aby dwa typy kodu do ze sobą współdziałać.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Proces programu Visual Basic różni się od wizualizacji C# procesu. Aby uzyskać więcej informacji, zobacz [jak: Udostępnianie kodu z VBA w Visual C&#35; projektu](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).

 Proces jest inny dla kodu w klasie elementu hosta, niż jest dla kodu w innych klas:

- [Udostępnianie kodu w klasie element hosta](#HostItemCode)

- [Udostępnianie kodu, który nie jest w klasie element hosta](#NonHostItem)

  ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak: Wywołać kod VSTO z kodu VBA? ](http://go.microsoft.com/fwlink/?LinkId=136757).

## <a name="HostItemCode"></a> Udostępnianie kodu w klasie element hosta
 Aby włączyć kodu VBA w celu wywołania kodu języka Visual Basic w klasie elementu hosta, należy ustawić **EnableVbaCallers** właściwości elementu hosta do **True**.

 Aby uzyskać wskazówki, który demonstruje sposób ujawnia metody klasy elementu hosta, a następnie wywołaj ją z kodu VBA, zobacz [instruktażu: Wywoływanie kodu z VBA w projektach Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md). Aby uzyskać więcej informacji na temat elementów hosta, zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md).

#### <a name="to-expose-code-in-a-host-item-to-vba"></a>Aby udostępnianie kodu w elemencie hosta z VBA

1. Otwórz lub Utwórz poziomu dokumentu [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projektu, który jest oparty na dokument programu Word, skoroszyt programu Excel lub szablon programu Excel, która obsługuje makr i zawierający kod VBA.

     Aby uzyskać więcej informacji na temat formatów plików dokumentów, które obsługuje makr, zobacz [łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).

    > [!NOTE]
    >  Nie można użyć tej funkcji w projektach szablon programu Word.

2. Upewnij się, że kod VBA w dokumencie może być uruchamiane bez monitowania użytkownika o włączenie makr. Kod VBA przez dodanie lokalizacji projektu pakietu Office do listy zaufanych lokalizacji w ustawieniach Centrum zaufania dla programu Word lub Excel można ufać.

3. Dodaj właściwości, metody lub zdarzenie, dla którego ma zostać uwidoczniona VBA do jednej z klas elementu hosta w projekcie i Zadeklaruj nowy element członkowski jako **publicznych**. Nazwa klasy zależy od aplikacji:

    - W programie project, klasa elementów hosta nosi nazwę `ThisDocument` domyślnie.

    - W projekcie programu Excel o nazwie klasy elementu hosta `ThisWorkbook`, `Sheet1`, `Sheet2`, i `Sheet3` domyślnie.

4. Ustaw **EnableVbaCallers** właściwość elementu hosta do **True**. Ta właściwość jest dostępna w **właściwości** okna, gdy element hosta jest otwarty w projektancie.

     Po ustawieniu tej właściwości program Visual Studio automatycznie ustawia **ReferenceAssemblyFromVbaProject** właściwości **True**.

    > [!NOTE]
    >  Jeśli skoroszyt lub dokument nie zawiera kodu VBA lub jeżeli kod VBA w dokumencie nie jest zaufane do uruchamiania, otrzymasz komunikat o błędzie, gdy ustawisz **EnableVbaCallers** właściwości **True**. Jest to spowodowane programu Visual Studio nie można modyfikować projektu VBA w dokumencie w takiej sytuacji.

5. Kliknij przycisk **OK** wiadomości, która jest wyświetlana. Ten komunikat przypomina o tym, że jeśli dodasz kod VBA do skoroszytu lub dokumentu, podczas uruchamiasz projekt z [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], kod VBA zostaną utracone podczas następnego, skompiluj projekt. Jest to spowodowane dokumentu w folderze wyjściowym kompilacji jest zastępowany za każdym razem, gdy kompilujesz projekt.

     W tym momencie program Visual Studio umożliwia skonfigurowanie projektu tak, aby wywołać projektu VBA w zestawie. Program Visual Studio dodaje również właściwość o nazwie `CallVSTOAssembly` do `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2`, lub `Sheet3` modułu w projekcie języka VBA. Ta właściwość umożliwia dostęp do publicznych elementów członkowskich klasy, które są udostępniane z VBA.

6. Skompiluj projekt.

## <a name="NonHostItem"></a> Udostępnianie kodu, który nie jest w klasie element hosta
 Aby włączyć kodu VBA w celu wywołania kodu języka Visual Basic, który nie jest w klasie elementu hosta, zmodyfikować kod, więc widoczne z VBA.

### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>Aby udostępnić kod, który nie jest klasą elementu hosta z VBA

1. Otwórz lub Utwórz poziomu dokumentu [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projektu, który jest oparty na dokument programu Word, skoroszyt programu Excel lub szablon programu Excel, która obsługuje makr i zawierający kod VBA.

     Aby uzyskać więcej informacji na temat formatów plików dokumentów, które obsługuje makr, zobacz [łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).

    > [!NOTE]
    >  Nie można użyć tej funkcji w projektach szablon programu Word.

2. Upewnij się, że kod VBA w dokumencie może być uruchamiane bez monitowania użytkownika o włączenie makr. Kod VBA przez dodanie lokalizacji projektu pakietu Office do listy zaufanych lokalizacji w ustawieniach Centrum zaufania dla programu Word lub Excel można ufać.

3. Dodawanie elementu członkowskiego, który chcesz udostępnić VBA publiczne klasy w projekcie i Zadeklaruj nowy element członkowski jako **publicznych**.

4. Zastosuj następujące <xref:System.Runtime.InteropServices.ComVisibleAttribute> i <xref:Microsoft.VisualBasic.ComClassAttribute> atrybutów do klasy, które wyświetlasz VBA. Te atrybuty widoczności klasy VBA.

    ```vb
    <Microsoft.VisualBasic.ComClass()> _
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _
    ```

5. Zastąp **GetAutomationObject** metody klasy elementu hosta w projekcie, aby zwrócić wystąpienia klasy, które wyświetlasz VBA. Poniższy przykład kodu zakłada, że wyświetlasz klasę o nazwie `DocumentUtilities` VBA.

    ```vb
    Protected Overrides Function GetAutomationObject() As Object
        Return New DocumentUtilities()
    End Function
    ```

6. Otwórz dokument (dla programu Word) lub Projektant arkusz (Excel) w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

7. W **właściwości** wybierz **ReferenceAssemblyFromVbaProject** właściwości i zmień wartość na **True**.

    > [!NOTE]
    >  Jeśli skoroszyt lub dokument nie zawiera kodu VBA lub jeżeli kod VBA w dokumencie nie jest zaufane do uruchamiania, otrzymasz komunikat o błędzie, gdy ustawisz **ReferenceAssemblyFromVbaProject** właściwość **True** . Jest to spowodowane programu Visual Studio nie można modyfikować projektu VBA w dokumencie w takiej sytuacji.

8. Kliknij przycisk **OK** wiadomości, która jest wyświetlana. Ten komunikat przypomina o tym, że jeśli dodasz kod VBA do skoroszytu lub dokumentu, podczas uruchamiasz projekt z [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], kod VBA zostaną utracone podczas następnego, skompiluj projekt. Jest to spowodowane dokumentu w folderze wyjściowym kompilacji jest zastępowany za każdym razem, gdy kompilujesz projekt.

     W tym momencie program Visual Studio umożliwia skonfigurowanie projektu tak, aby wywołać projektu VBA w zestawie. Program Visual Studio dodaje także metodę o nazwie `GetManagedClass` do projektu VBA. Tę metodę można wywołać z dowolnego miejsca w projekcie VBA dostępu do tej klasy, która widoczna VBA.

9. Skompiluj projekt.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md)
- [Przewodnik: Wywoływanie kodu z VBA w projektach Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [Instrukcje: Udostępnianie kodu z VBA w Visual C&#35; projektu](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
