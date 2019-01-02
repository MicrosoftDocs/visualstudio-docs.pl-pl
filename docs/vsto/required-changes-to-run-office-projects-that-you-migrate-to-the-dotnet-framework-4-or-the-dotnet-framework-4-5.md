---
title: Zmiany wymagane w celu uruchamiania projektów pakietu Office, które przenoszonych do oprogramowania .NET Framework 4 lub .NET Framework 4.5
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 819a3f1c0ea4541bee55dca2402cac6dbf9848cc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917621"
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Zmiany wymagane w celu uruchamiania projektów pakietu Office, które przenoszonych do oprogramowania .NET Framework 4 lub .NET Framework 4.5
  Jeśli platforma docelowa projektu pakietu Office jest zmieniana na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszy z wcześniejszej wersji programu .NET Framework, należy wykonać następujące zadania, aby upewnić się, że rozwiązanie można uruchomić na komputerze deweloperskim i na komputerach użytkowników końcowych:  
  
- Usuń <xref:System.Security.SecurityTransparentAttribute> z projektu w przypadku uaktualnienia z programu Visual Studio 2008.  
  
- Wykonaj **czysty** polecenia w programie Visual Studio, aby można było uruchomić ani debugować projektu na komputerze deweloperskim.  
  
- Aktualizacja programu .NET Framework wymagań wstępnych dla projektu.  
  
- Użytkownicy końcowi również należy ponownie zainstalować rozwiązania, jeśli została wcześniej wdrożona przy użyciu technologii ClickOnce, przed zmianą platformy docelowej.  
  
  Aby uzyskać więcej informacji na temat każdego z tych zadań zobacz poniższe sekcje odpowiednie.  
  
## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Usuń atrybut atrybutów SecurityTransparent projektach, które uaktualniania z programu Visual Studio 2008  
 Jeśli uaktualniasz projekt Office z programu Visual Studio 2008 i docelowa platforma projektu później zmieni się na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej, musisz usunąć <xref:System.Security.SecurityTransparentAttribute> z projektu. Program Visual Studio nie są automatycznie usuwane ten atrybut za Ciebie. Jeśli ten atrybut nie zostanie usunięty, otrzymasz komunikat o błędzie, podczas kompilowania projektu.  
  
 Aby uzyskać więcej informacji o warunkach, w których program Visual Studio można zmienić platformę docelową uaktualnionego projektu do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], zobacz [uaktualnianie i migracja rozwiązań pakietu Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
#### <a name="to-remove-the-securitytransparentattribute"></a>Aby usunąć atrybut SecurityTransparentAttribute  
  
1.  Otwarty projekt w programie Visual Studio, otwórz **Eksploratora rozwiązań**.  
  
2.  W obszarze **właściwości** węzeł (C#) lub **mój projekt** węzeł (Visual Basic), kliknij dwukrotnie plik kodu AssemblyInfo, aby otworzyć go w edytorze kodu.  
  
    > [!NOTE]  
    >  W projektach języka Visual Basic, należy kliknąć przycisk **Pokaż wszystkie pliki** znajdujący się w **Eksploratora rozwiązań** aby zobaczyć plik kodu AssemblyInfo.  
  
3.  Znajdź <xref:System.Security.SecurityTransparentAttribute> i usuń go z pliku lub komentarz dotyczący działanie.  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Wykonaj czystą polecenie, aby debugować lub uruchomić projekt na komputerze deweloperskim  
 Jeśli został zbudowany projektu pakietu Office, przed zmianą platformy docelowej projektu do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej, należy wykonać **czysty** poleceń i skompiluj ponownie projekt po zmianie platformy docelowej. Jeśli nie wykonuj **czysty** polecenia zostanie wyświetlony <xref:System.Runtime.InteropServices.COMException> podczas debugowania lub uruchomienia projektu przebudowanymi pod inne środowisko.  
  
 Aby uzyskać więcej informacji na temat **czysty** polecenia, zobacz [rozwiązań kompilacji pakietu Office](../vsto/building-office-solutions.md).  
  
## <a name="update-the-prerequisites-for-deployment"></a>Wymagania wstępne dotyczące wdrażania aktualizacji  
 Jeśli przekierowanie projektu pakietu Office w taki sposób, aby [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej, należy również zaktualizować odpowiednie wstępnie wymaganego programu .NET Framework w **wymagania wstępne** okno dialogowe. W przeciwnym razie wdrażanie ClickOnce lub projekt InstallShield Limited Edition wyszukuje i instaluje poprzedniej wersji programu .NET Framework.  
  
 Aby uzyskać więcej informacji o aktualizowaniu wymagania wstępne dotyczące wdrażania na komputerach użytkowników końcowych, zobacz [jak: Instalowanie wymagań wstępnych na komputerach użytkowników końcowych do uruchamiania rozwiązań pakietu Office](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
## <a name="reinstall-solutions-on-end-user-computers"></a>Ponownie zainstaluj rozwiązania na komputerach użytkowników końcowych  
 Jeśli użycie technologii ClickOnce do wdrażania rozwiązania pakietu Office, który jest przeznaczony dla .NET Framework 3.5, a następnie zmień platformę docelową projektu, aby [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, użytkownicy końcowi należy odinstalować rozwiązania, a następnie zainstaluj ponownie rozwiązanie po ponownie ją opublikować. Jeśli publikujesz przekierowane rozwiązanie, a rozwiązanie jest aktualizowana na komputerach użytkowników końcowych, użytkownicy końcowi będą otrzymywać <xref:System.Runtime.InteropServices.COMException> uruchamiania do zaktualizowane rozwiązanie.  
  
## <a name="see-also"></a>Zobacz także  
 [Migrowanie rozwiązań pakietu Office do wersji programu .NET Framework 4 lub nowszej](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
