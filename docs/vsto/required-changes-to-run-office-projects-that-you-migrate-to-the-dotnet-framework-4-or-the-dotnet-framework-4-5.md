---
title: Zmiany wymagane przez projekty pakietu Office migrowane do programu .NET 4,5
description: Informacje o zmianach, które należy wprowadzić w projekcie, jeśli struktura docelowa zmieni się na .NET Framework 4 lub nowszą ze starszej wersji .NET Framework.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4fbe3c311e734cc076ab898544470c3e27e91795
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943721"
---
# <a name="changes-required-for-office-projects-migrated-to-net-45"></a>Zmiany wymagane przez projekty pakietu Office migrowane do programu .NET 4,5

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

 Aby uzyskać więcej informacji na temat aktualizacji wymagań wstępnych dotyczących wdrażania na komputerach użytkowników końcowych, zobacz [How to: Install Preinstallations on End Computers to the user Solutions](/previous-versions/bb608608(v=vs.110)).

## <a name="reinstall-solutions-on-end-user-computers"></a>Ponowne instalowanie rozwiązań na komputerach użytkowników końcowych
 Jeśli używasz technologii ClickOnce do wdrożenia rozwiązania pakietu Office przeznaczonego dla .NET Framework 3,5, a następnie przekierujesz projekt do programu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszego, użytkownicy końcowi muszą odinstalować rozwiązanie, a następnie ponownie zainstalować rozwiązanie po ponownym opublikowaniu. Jeśli ponownie opublikowano rozwiązanie przekierowania, a rozwiązanie zostanie zaktualizowane na komputerach użytkowników końcowych, użytkownicy końcowi otrzymają komunikat, <xref:System.Runtime.InteropServices.COMException> gdy uruchomili zaktualizowane rozwiązanie.

## <a name="see-also"></a>Zobacz też
- [Migrowanie rozwiązań pakietu Office do .NET Framework 4 lub nowszego](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)