---
title: Zmiany wymagane przez projekty pakietu Office migrowane do .NET Framework 4, 4,5
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 82ae3f8a43b65e6ff617192dc38149691d229455
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "66836057"
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Wymagane zmiany w celu uruchomienia projektów pakietu Office migrowanych do .NET Framework 4 lub .NET Framework 4,5
  Jeśli docelowa platforma projektu pakietu Office zostanie zmieniona na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub w późniejszym czasie ze starszej wersji .NET Framework, należy wykonać następujące zadania, aby upewnić się, że rozwiązanie można uruchomić na komputerze deweloperskim i na komputerach użytkowników końcowych:

- Usuń <xref:System.Security.SecurityTransparentAttribute> z projektu, jeśli został uaktualniony z programu Visual Studio 2008.

- Wykonaj polecenie **Clean** w programie Visual Studio, aby móc uruchamiać lub debugować projekt na komputerze deweloperskim.

- Zaktualizuj .NET Framework wymaganie wstępne dla projektu.

- Użytkownicy końcowi muszą również ponownie zainstalować rozwiązanie, jeśli wcześniej zostały wdrożone przy użyciu technologii ClickOnce przed zmianą platformy docelowej.

  Aby uzyskać więcej informacji na temat każdego z tych zadań, zobacz odpowiednie sekcje poniżej.

## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Usuń atrybut SecurityTransparent z projektów uaktualnianych z programu Visual Studio 2008
 W przypadku uaktualniania projektu pakietu Office z programu Visual Studio 2008 i docelowej platformy projektu następnie zmiany w programie [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym należy usunąć <xref:System.Security.SecurityTransparentAttribute> z projektu. Program Visual Studio nie usuwa automatycznie tego atrybutu. Jeśli ten atrybut nie zostanie usunięty, podczas kompilowania projektu zostanie wyświetlony komunikat o błędzie.

 Aby uzyskać więcej informacji na temat warunków, w których program Visual Studio może zmienić platformę docelową uaktualnionego projektu na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , zobacz [uaktualnianie i migrowanie rozwiązań pakietu Office](../vsto/upgrading-and-migrating-office-solutions.md).

#### <a name="to-remove-the-securitytransparentattribute"></a>Aby usunąć SecurityTransparentAttribute

1. Po otwarciu projektu w programie Visual Studio Otwórz **Eksplorator rozwiązań**.

2. W węźle **Właściwości** (dla języka C#) lub węzła **mój projekt** (dla Visual Basic) kliknij dwukrotnie plik kodu AssemblyInfo, aby otworzyć go w edytorze kodu.

    > [!NOTE]
    > W projektach Visual Basic należy kliknąć przycisk **Pokaż wszystkie pliki** w **Eksplorator rozwiązań** , aby wyświetlić plik kodu AssemblyInfo.

3. Znajdź <xref:System.Security.SecurityTransparentAttribute> i usuń go z pliku lub Dodaj do niego komentarz.

    ```vb
    <Assembly: SecurityTransparent()>
    ```

    ```csharp
    [assembly: SecurityTransparent()]
    ```

## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Wykonaj polecenie Clean, aby debugować lub uruchomić projekt na komputerze deweloperskim
 Jeśli projekt pakietu Office został skompilowany przed zmianą platformy docelowej projektu na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, należy wykonać **czyste** polecenie, a następnie ponownie skompilować projekt po zmianie platformy docelowej. Jeśli nie wykonuj **czystego** polecenia, otrzymasz komunikat <xref:System.Runtime.InteropServices.COMException> podczas próby debugowania lub uruchomienia projektu przekierowania.

 Aby uzyskać więcej informacji na temat polecenia **Clean** , zobacz [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).

## <a name="update-the-prerequisites-for-deployment"></a>Aktualizowanie wymagań wstępnych dotyczących wdrożenia
 W przypadku przekierowania projektu pakietu Office do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszego, należy również zaktualizować odpowiednie wymagania wstępne .NET Framework w oknie dialogowym **wstępnie wymagane składniki** . W przeciwnym razie wdrożenie ClickOnce lub program InstallShield Limited Edition sprawdza i instaluje poprzednią wersję .NET Framework.

 Aby uzyskać więcej informacji na temat aktualizacji wymagań wstępnych dotyczących wdrażania na komputerach użytkowników końcowych, zobacz [How to: Install Preinstallations on End Computers to the user Solutions](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).

## <a name="reinstall-solutions-on-end-user-computers"></a>Ponowne instalowanie rozwiązań na komputerach użytkowników końcowych
 Jeśli używasz technologii ClickOnce do wdrożenia rozwiązania pakietu Office przeznaczonego dla .NET Framework 3,5, a następnie przekierujesz projekt do programu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszego, użytkownicy końcowi muszą odinstalować rozwiązanie, a następnie ponownie zainstalować rozwiązanie po ponownym opublikowaniu. Jeśli ponownie opublikowano rozwiązanie przekierowania, a rozwiązanie zostanie zaktualizowane na komputerach użytkowników końcowych, użytkownicy końcowi otrzymają komunikat, <xref:System.Runtime.InteropServices.COMException> gdy uruchomili zaktualizowane rozwiązanie.

## <a name="see-also"></a>Zobacz też
- [Migrowanie rozwiązań pakietu Office do .NET Framework 4 lub nowszego](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
