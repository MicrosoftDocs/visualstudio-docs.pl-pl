---
title: 'Instrukcje: Otwieranie rozwiązań pakietu Office bez uruchamiania kodu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7684fd2d01d0151798c9e59c593e3e0c2acb95b1
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53646909"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Instrukcje: Otwieranie rozwiązań pakietu Office bez uruchamiania kodu
  Rozwiązania Microsoft Office, utworzone za pomocą rozszerzeń kodu zarządzanego jest uruchamiany nawet wtedy, gdy ustawienia zabezpieczeń w aplikacji pakietu Office przez użytkownika końcowego jest ustawiony na wysoki. Jest to spowodowane zabezpieczenie kodu zestawu .NET jest zarządzana przez program Microsoft .NET Framework, nie przez Microsoft Office.  
  
 Istnieją jednak czasy, kiedy warto otworzyć dokument bez uruchamiania kodu. Na przykład kod, który jest uruchamiany po otwarciu dokumentu może zmienić zawartość, ale ma zostać zaktualizowany dokument wyglądu przed zmian w kodzie. Lub możesz chcieć wysłać dokument niektóre informacje w nim innej, a nie chcesz, aby kod, aby uruchomić i być może zmienić zawartość.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Istnieje kilka sposobów, aby otworzyć dokument lub skoroszyt zawierający rozszerzenia kodu zarządzanego bez uruchamiania kodu zestawu.  
  
## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Aby pominąć zestawu przy użyciu klawisza Shift  
  
-   Otwórz dokumenty i skoroszyty z **pliku** menu, przytrzymując naciśnięty **Shift** klawisz, aby uniemożliwić wywoływanie zdarzeń inicjowania, podczas otwierania dokumentu programu Word i Excel.  
  
    > [!NOTE]  
    >  Jeśli możesz otworzyć dokument lub skoroszyt z **wprowadzenie** okienka zadań, przytrzymując **Shift** kodu nie obejścia. Ponadto przytrzymując wciśnięty klawisz SHIFT nie zapobiega zdarzenia są zgłaszane po otwarciu dokumentu.  
  
     Ta metoda jest przydatna, jeśli chcesz otworzyć dokument, aby wprowadzić zmiany, bez konieczności pisania kodu, uruchamiania i zmieniania dokumentu najpierw.  
  
## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Aby pominąć zestawu, zmiana nazwy lub usuwanie go  
  
-   Jeśli masz odpowiednie uprawnienia na komputerze, na którym znajduje się zestaw można zmienić lub usunąć zestaw, dokument lub skoroszyt nie można odnaleźć. Powoduje to błąd są zgłaszane w każdym otwarciu dokumentu pakietu Office.  
  
     Jeśli rozwiązanie jest używane przez wiele osób, ta metoda uniemożliwia rozwiązanie działa dla wszystkich z nich. Może to być przydatne, jeśli problem zostanie znaleziony w kod lub odwołania server i chcesz uniemożliwić użytkownikom wszystkich jej wykonanie.  
  
## <a name="see-also"></a>Zobacz także  
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Manifesty aplikacji i wdrożenia w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  