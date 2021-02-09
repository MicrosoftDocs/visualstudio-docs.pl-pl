---
title: 'Instrukcje: Uwidacznianie kodu w języku VBA w projekcie Visual Basic'
description: Dowiedz się, jak udostępnić kod w projekcie Visual Basic do kodu Visual Basic for Applications (VBA), jeśli chcesz, aby dwa typy kodu mogły współdziałać ze sobą.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 69ef8b47ac4038b466d0ebf859832bd4363403cd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913498"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>Instrukcje: Uwidacznianie kodu w języku VBA w projekcie Visual Basic
  Można uwidocznić kod w [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projekcie do kodu Visual Basic for Applications (VBA), jeśli chcesz, aby dwa typy kodu współpracowali ze sobą.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Proces Visual Basic różni się od procesu Visual C#. Aby uzyskać więcej informacji, zobacz [How to: Uwidacznianie kodu w języku VBA w projekcie Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).

 Proces jest różny dla kodu w klasie elementów hosta niż w przypadku kodu w innych klasach:

- [Uwidacznianie kodu w klasie elementów hosta](#HostItemCode)

- [Uwidacznianie kodu, który nie znajduje się w klasie elementów hosta](#NonHostItem)

## <a name="expose-code-in-a-host-item-class"></a><a name="HostItemCode"></a> Uwidacznianie kodu w klasie elementów hosta
 Aby włączyć kod języka VBA do wywoływania Visual Basic kodu w klasie elementu hosta, ustaw właściwość **EnableVbaCallers** elementu hosta na **wartość true**.

 Aby zapoznać się z przewodnikiem, który ilustruje sposób uwidocznienia metody klasy elementu hosta, a następnie Wywołaj ją z poziomu języka VBA, zobacz [Przewodnik: wywoływanie kodu z VBA w projekcie Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md). Aby uzyskać więcej informacji na temat elementów hosta, zobacz [Omówienie elementów hosta i formantów hosta](../vsto/host-items-and-host-controls-overview.md).

#### <a name="to-expose-code-in-a-host-item-to-vba"></a>Aby uwidocznić kod w elemencie hosta w języku VBA

1. Otwórz lub Utwórz projekt na poziomie dokumentu [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] oparty na dokumencie programu Word, skoroszycie programu Excel lub szablonie programu Excel, który obsługuje makra i który zawiera już kod języka VBA.

     Aby uzyskać więcej informacji na temat formatów plików dokumentów, które obsługują makra, zobacz [łączenie języka VBA i dostosowań na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).

    > [!NOTE]
    > Tej funkcji nie można używać w projektach szablonów programu Word.

2. Upewnij się, że kod VBA w dokumencie może być uruchamiany bez monitowania użytkownika o włączenie makr. Można ufać kodzie VBA do uruchomienia przez dodanie lokalizacji projektu pakietu Office do listy zaufanych lokalizacji w ustawieniach Centrum zaufania dla programu Word lub Excel.

3. Dodaj właściwość, metodę lub zdarzenie, które chcesz uwidocznić w języku VBA, do jednej z klas elementów hosta w projekcie i Zadeklaruj nowy element członkowski jako **publiczny**. Nazwa klasy zależy od aplikacji:

    - W projekcie programu Word Klasa elementu hosta jest domyślnie nazywana `ThisDocument` .

    - W projekcie programu Excel klasy elementów hosta mają `ThisWorkbook` Domyślnie nazwy, `Sheet1` , `Sheet2` i `Sheet3` .

4. Ustaw właściwość **EnableVbaCallers** dla elementu hosta na **wartość true**. Ta właściwość jest dostępna w oknie **Właściwości** , gdy element hosta jest otwarty w projektancie.

     Po ustawieniu tej właściwości program Visual Studio automatycznie ustawia właściwość **ReferenceAssemblyFromVbaProject** na **true**.

    > [!NOTE]
    > Jeśli skoroszyt lub dokument nie zawiera jeszcze kodu VBA lub jeśli kod VBA w dokumencie nie jest zaufany do uruchomienia, zostanie wyświetlony komunikat o błędzie po ustawieniu właściwości **EnableVbaCallers** na **true**. Wynika to z faktu, że program Visual Studio nie może zmodyfikować projektu VBA w dokumencie w takiej sytuacji.

5. Kliknij przycisk **OK** w wyświetlonym komunikacie. Ten komunikat przypomina, że jeśli dodasz kod języka VBA do skoroszytu lub dokumentu podczas uruchamiania projektu z [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , kod VBA zostanie utracony przy następnym skompilowaniu projektu. Wynika to z faktu, że dokument w folderze danych wyjściowych kompilacji jest zastępowany za każdym razem, gdy kompilujesz projekt.

     W tym momencie program Visual Studio konfiguruje projekt, tak aby projekt VBA mógł wywołać do zestawu. Program Visual Studio dodaje również właściwość o nazwie `CallVSTOAssembly` do `ThisDocument` `ThisWorkbook` modułu,,,, `Sheet1` `Sheet2` lub `Sheet3` w projekcie VBA. Ta właściwość służy do uzyskiwania dostępu do publicznych członków klasy, które zostały uwidocznione w języku VBA.

6. Skompiluj projekt.

## <a name="expose-code-that-is-not-in-a-host-item-class"></a><a name="NonHostItem"></a> Uwidacznianie kodu, który nie znajduje się w klasie elementów hosta
 Aby włączyć kod języka VBA do wywoływania Visual Basic kodu, który nie znajduje się w klasie elementów hosta, zmodyfikuj kod, tak aby był widoczny dla języka VBA.

### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>Aby uwidocznić kod, który nie znajduje się w klasie elementu hosta do języka VBA

1. Otwórz lub Utwórz projekt na poziomie dokumentu [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] oparty na dokumencie programu Word, skoroszycie programu Excel lub szablonie programu Excel, który obsługuje makra i który zawiera już kod języka VBA.

     Aby uzyskać więcej informacji na temat formatów plików dokumentów, które obsługują makra, zobacz [łączenie języka VBA i dostosowań na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).

    > [!NOTE]
    > Tej funkcji nie można używać w projektach szablonów programu Word.

2. Upewnij się, że kod VBA w dokumencie może być uruchamiany bez monitowania użytkownika o włączenie makr. Można ufać kodzie VBA do uruchomienia przez dodanie lokalizacji projektu pakietu Office do listy zaufanych lokalizacji w ustawieniach Centrum zaufania dla programu Word lub Excel.

3. Dodaj element członkowski, który ma zostać ujawniony w języku VBA, do klasy publicznej w projekcie i Zadeklaruj nowy element członkowski jako **publiczny**.

4. Zastosuj następujące <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybuty i <xref:Microsoft.VisualBasic.ComClassAttribute> do klasy, która jest uwidaczniana w języku VBA. Te atrybuty sprawiają, że Klasa jest widoczna dla języka VBA.

    ```vb
    <Microsoft.VisualBasic.ComClass()> _
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _
    ```

5. Zastąp metodę **GetAutomationObject** klasy elementu hosta w projekcie, aby zwrócić wystąpienie klasy, która jest uwidaczniana w języku VBA. W poniższym przykładzie kodu założono, że ujawniasz klasę o nazwie `DocumentUtilities` do VBA.

    ```vb
    Protected Overrides Function GetAutomationObject() As Object
        Return New DocumentUtilities()
    End Function
    ```

6. Otwórz dokument (dla programu Word) lub projektanta arkusza (dla programu Excel) w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

7. W oknie **Właściwości** wybierz właściwość **ReferenceAssemblyFromVbaProject** i zmień wartość na **true**.

    > [!NOTE]
    > Jeśli skoroszyt lub dokument nie zawiera jeszcze kodu VBA lub jeśli kod VBA w dokumencie nie jest zaufany do uruchomienia, zostanie wyświetlony komunikat o błędzie po ustawieniu właściwości **ReferenceAssemblyFromVbaProject** na **true**. Wynika to z faktu, że program Visual Studio nie może zmodyfikować projektu VBA w dokumencie w takiej sytuacji.

8. Kliknij przycisk **OK** w wyświetlonym komunikacie. Ten komunikat przypomina, że jeśli dodasz kod języka VBA do skoroszytu lub dokumentu podczas uruchamiania projektu z [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , kod VBA zostanie utracony przy następnym skompilowaniu projektu. Wynika to z faktu, że dokument w folderze danych wyjściowych kompilacji jest zastępowany za każdym razem, gdy kompilujesz projekt.

     W tym momencie program Visual Studio konfiguruje projekt, tak aby projekt VBA mógł wywołać do zestawu. Program Visual Studio dodaje również metodę o nazwie `GetManagedClass` do projektu VBA. Możesz wywołać tę metodę z dowolnego miejsca w projekcie VBA, aby uzyskać dostęp do klasy uwidocznionej w języku VBA.

9. Skompiluj projekt.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Łączenie języka VBA i dostosowań na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md)
- [Przewodnik: wywoływanie kodu z VBA w projekcie Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [Instrukcje: Uwidacznianie kodu w języku VBA w projekcie programu Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
