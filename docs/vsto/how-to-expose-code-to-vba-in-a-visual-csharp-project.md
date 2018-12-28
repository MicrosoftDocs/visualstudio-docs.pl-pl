---
title: 'Instrukcje: Udostępnianie kodu z VBA w C# projektu'
ms.custom: seodec18
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1f0b3f004f6aebed6426238a081369c7d50e15f5
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648512"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Instrukcje: Udostępnianie kodu z VBA w wizualizacji C# projektu
  Można udostępnić kod w wizualizacji C# projekt języka Visual Basic for Applications (VBA) kod Jeśli chcesz, aby dwa typy kodu do ze sobą współdziałać.  
  
 Element wizualny C# proces różni się od procesu języka Visual Basic. Aby uzyskać więcej informacji, zobacz [jak: Udostępnianie kodu z VBA w projektach Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="expose-code-in-a-visual-c-project"></a>Udostępnianie kodu w wizualizacji C# projektu  
 Aby włączyć kod VBA w celu wywołania kodu w wizualizacji C# projektu, zmodyfikować kod, aby była widoczna dla modelu COM, a następnie ustaw **ReferenceAssemblyFromVbaProject** właściwości **True** w projektancie.  
  
 Aby uzyskać wskazówki, który demonstruje sposób wywołania metody w wizualizacji C# projektu z kodu VBA, zobacz [wskazówki: Wywoływanie kodu z VBA w Visual C&#35; projektu](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Do udostępnienia kodu w wizualizacji C# projektu VBA  
  
1. Otwórz lub Utwórz projekt poziomie dokumentu, który jest oparty na dokument programu Word, skoroszyt programu Excel lub szablon programu Excel, która obsługuje makr i zawierający kod VBA.  
  
    Aby uzyskać więcej informacji na temat formatów plików dokumentów, które obsługuje makr, zobacz [łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).  
  
   > [!NOTE]  
   >  Nie można użyć tej funkcji w projektach szablon programu Word.  
  
2. Upewnij się, że kod VBA w dokumencie może być uruchamiane bez monitowania użytkownika o włączenie makr. Kod VBA przez dodanie lokalizacji projektu pakietu Office do listy zaufanych lokalizacji w ustawieniach Centrum zaufania dla programu Word lub Excel można ufać.  
  
3. Dodawanie elementu członkowskiego, który chcesz udostępnić VBA publiczne klasy w projekcie i Zadeklaruj nowy element członkowski jako **publicznych**.  
  
4. Zastosuj następujące <xref:System.Runtime.InteropServices.ComVisibleAttribute> i <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybutów do klasy, które wyświetlasz VBA. Te atrybuty widoczności klasy dla modelu COM, ale bez generowania interfejsu klasy.  
  
   ```csharp  
   [System.Runtime.InteropServices.ComVisible(true)]  
   [System.Runtime.InteropServices.ClassInterface(  
       System.Runtime.InteropServices.ClassInterfaceType.None)]  
   ```  
  
5. Zastąp **GetAutomationObject** metody klasy elementu hosta w projekcie, aby zwrócić wystąpienia klasy, które wyświetlasz VBA:  
  
   - Jeśli wyświetlasz klasy elementu obsługującej VBA zastępują **GetAutomationObject** metodę, która należy do tej klasy, a następnie zwraca bieżące wystąpienie klasy.  
  
     ```csharp  
     protected override object GetAutomationObject()  
     {  
         return this;  
     }  
     ```  
  
   - Jeśli wyświetlasz klasę, która nie jest elementem hosta z VBA zastępują **GetAutomationObject** metoda dowolnego hosta elementu w projekcie i zwraca wystąpienie klasy elementu niezwiązanych z hostem. Na przykład, poniższy kod przyjęto założenie, że wyświetlasz klasę o nazwie `DocumentUtilities` VBA.  
  
     ```csharp  
     protected override object GetAutomationObject()  
     {  
         return new DocumentUtilities();  
     }  
     ```  
  
     Aby uzyskać więcej informacji na temat elementów hosta, zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md).  
  
6. Wyodrębnij interfejs z klasy, które wyświetlasz VBA. W **Wyodrębnij interfejs** okna dialogowego Wybierz publiczne elementy członkowskie, które mają zostać uwzględnione w deklaracji interfejsu. Aby uzyskać więcej informacji, zobacz [wyodrębniania interfejsu Refaktoryzacja](../ide/reference/extract-interface.md).
  
7. Dodaj **publicznych** — słowo kluczowe z deklaracją interfejsu.  
  
8. Ustawienie widoczności interfejsu COM przez dodanie poniższego <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybutu do interfejsu.  
  
   ```csharp  
   [System.Runtime.InteropServices.ComVisible(true)]  
   ```  
  
9. Otwórz dokument (dla programu Word) lub arkusz (Excel) w projektancie w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
10. W **właściwości** wybierz **ReferenceAssemblyFromVbaProject** właściwości i zmień wartość na **True**.  
  
    > [!NOTE]  
    >  Jeśli skoroszyt lub dokument nie zawiera kodu VBA, lub jeżeli kod VBA w dokumencie nie jest zaufane do uruchamiania, otrzymasz komunikat o błędzie, gdy ustawisz **ReferenceAssemblyFromVbaProject** właściwość **True**. Jest to spowodowane programu Visual Studio nie można modyfikować projektu VBA w dokumencie w takiej sytuacji.  
  
11. Kliknij przycisk **OK** wiadomości, która jest wyświetlana. Ten komunikat przypomina o tym, że jeśli dodasz VBA kodu w skoroszycie lub dokumentów podczas uruchamiania projektu z [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], kod VBA zostaną utracone przy następnym uruchomieniu, skompiluj projekt. Jest to spowodowane dokumentu w kompilacji, dane wyjściowe, że folder jest zastępowany podczas każdego kompilowania projektu.  
  
     W tym momencie program Visual Studio umożliwia skonfigurowanie projektu tak, aby wywołać projektu VBA w zestawie. Program Visual Studio dodaje także metodę o nazwie `GetManagedClass` do projektu VBA. Tę metodę można wywołać z dowolnego miejsca w projekcie VBA dostępu do tej klasy, która widoczna VBA.  
  
12. Skompiluj projekt.  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md)   
 [Przewodnik: Wywoływanie kodu z VBA w Visual C&#35; projektu](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Instrukcje: Udostępnianie kodu z VBA w projektach Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  