---
title: 'Instrukcje: Uwidacznianie kodu w języku VBA w projekcie w języku C#'
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 21d7672d3c08012e75d73ee8bf4d9816b850eb2c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544836"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Instrukcje: Uwidacznianie kodu w języku VBA w projekcie Visual C#
  Można uwidocznić kod w projekcie Visual C# do kodu Visual Basic for Applications (VBA), jeśli chcesz, aby dwa typy kodu współpracowali ze sobą.

 Proces Visual C# różni się od procesu Visual Basic. Aby uzyskać więcej informacji, zobacz [How to: Uwidacznianie kodu w języku VBA w projekcie Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="expose-code-in-a-visual-c-project"></a>Uwidacznianie kodu w projekcie Visual C#
 Aby włączyć kod języka VBA do wywoływania kodu w projekcie Visual C#, zmodyfikuj kod, tak aby był widoczny dla modelu COM, a następnie ustaw właściwość **ReferenceAssemblyFromVbaProject** na **wartość true** w projektancie.

 Aby zapoznać się z przewodnikiem, który pokazuje, jak wywołać metodę w projekcie Visual C# z języka VBA, zobacz [Przewodnik: wywoływanie kodu z VBA w projekcie Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).

### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Aby uwidocznić kod w projekcie Visual C# do języka VBA

1. Otwórz lub Utwórz projekt na poziomie dokumentu oparty na dokumencie programu Word, skoroszycie programu Excel lub szablonie programu Excel, który obsługuje makra i który zawiera już kod języka VBA.

    Aby uzyskać więcej informacji na temat formatów plików dokumentów, które obsługują makra, zobacz [łączenie języka VBA i dostosowań na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).

   > [!NOTE]
   > Tej funkcji nie można używać w projektach szablonów programu Word.

2. Upewnij się, że kod VBA w dokumencie może być uruchamiany bez monitowania użytkownika o włączenie makr. Można ufać kodzie VBA do uruchomienia przez dodanie lokalizacji projektu pakietu Office do listy zaufanych lokalizacji w ustawieniach Centrum zaufania dla programu Word lub Excel.

3. Dodaj element członkowski, który ma zostać ujawniony w języku VBA, do klasy publicznej w projekcie i Zadeklaruj nowy element członkowski jako **publiczny**.

4. Zastosuj następujące <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybuty i <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> do klasy, która jest uwidaczniana w języku VBA. Te atrybuty sprawiają, że Klasa jest widoczna dla modelu COM, ale bez generowania interfejsu klasy.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   [System.Runtime.InteropServices.ClassInterface(
       System.Runtime.InteropServices.ClassInterfaceType.None)]
   ```

5. Zastąp metodę **GetAutomationObject** klasy elementu hosta w projekcie, aby zwrócić wystąpienie klasy, która jest uwidaczniana w języku VBA:

   - Jeśli ujawniasz klasę elementu hosta do języka VBA, Zastąp metodę **GetAutomationObject** , która należy do tej klasy, i zwróci bieżące wystąpienie klasy.

     ```csharp
     protected override object GetAutomationObject()
     {
         return this;
     }
     ```

   - Jeśli ujawniasz klasę, która nie jest elementem hosta w języku VBA, Zastąp metodę **GetAutomationObject** dowolnego elementu hosta w projekcie i zwróć wystąpienie klasy elementów niebędących hostami. Na przykład poniższy kod założono, że ujawniasz klasę o nazwie `DocumentUtilities` do VBA.

     ```csharp
     protected override object GetAutomationObject()
     {
         return new DocumentUtilities();
     }
     ```

     Aby uzyskać więcej informacji na temat elementów hosta, zobacz [Omówienie elementów hosta i formantów hosta](../vsto/host-items-and-host-controls-overview.md).

6. Wyodrębnij interfejs z klasy, która jest uwidaczniana w języku VBA. W oknie dialogowym **wyodrębnianie interfejsu** wybierz publiczne elementy członkowskie, które mają zostać uwzględnione w deklaracji interfejsu. Aby uzyskać więcej informacji, zobacz [wyodrębnianie interfejsu refaktoryzacji](../ide/reference/extract-interface.md).

7. Dodaj słowo kluczowe **Public** do deklaracji interfejsu.

8. Ustaw interfejs jako widoczny dla modelu COM, dodając <xref:System.Runtime.InteropServices.ComVisibleAttribute> do interfejsu następujący atrybut.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   ```

9. Otwórz dokument (dla programu Word) lub arkusz (dla programu Excel) w projektancie w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

10. W oknie **Właściwości** wybierz właściwość **ReferenceAssemblyFromVbaProject** i zmień wartość na **true**.

    > [!NOTE]
    > Jeśli skoroszyt lub dokument nie zawiera jeszcze kodu VBA lub jeśli kod VBA w dokumencie nie jest zaufany do uruchomienia, zostanie wyświetlony komunikat o błędzie po ustawieniu właściwości **ReferenceAssemblyFromVbaProject** na **true**. Wynika to z faktu, że program Visual Studio nie może zmodyfikować projektu VBA w dokumencie w takiej sytuacji.

11. Kliknij przycisk **OK** w wyświetlonym komunikacie. Ten komunikat przypomina, że jeśli dodasz kod języka VBA do skoroszytu lub dokumentu podczas uruchamiania projektu z [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , kod VBA zostanie utracony przy następnym skompilowaniu projektu. Wynika to z faktu, że dokument w folderze danych wyjściowych kompilacji jest zastępowany za każdym razem, gdy kompilujesz projekt.

     W tym momencie program Visual Studio konfiguruje projekt, tak aby projekt VBA mógł wywołać do zestawu. Program Visual Studio dodaje również metodę o nazwie `GetManagedClass` do projektu VBA. Możesz wywołać tę metodę z dowolnego miejsca w projekcie VBA, aby uzyskać dostęp do klasy uwidocznionej w języku VBA.

12. Skompiluj projekt.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Łączenie języka VBA i dostosowań na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md)
- [Przewodnik: wywoływanie kodu z VBA w projekcie Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Instrukcje: Uwidacznianie kodu w języku VBA w projekcie Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
