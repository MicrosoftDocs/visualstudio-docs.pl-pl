---
title: Kompilowanie i debugowanie rozwiązań programu SharePoint | Microsoft Docs
description: Dowiedz się, jak tworzyć i debugować rozwiązania programu SharePoint oraz zrozumieć, jak różni się od kompilowania i debugowania innych typów projektów w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f6801f6b60d2ef522385ecdf290d0a1913bd6df2
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850224"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Kompilowanie i debugowanie rozwiązań SharePoint
  Ogólnie rzecz biorąc, kompilowanie i debugowanie rozwiązań programu SharePoint jest takie samo jak Kompilowanie i debugowanie innych typów projektów w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . W tematach w tej sekcji opisano różnice, które istnieją.

## <a name="project-output-for-sharepoint-solutions"></a>Dane wyjściowe projektu dla rozwiązań SharePoint
 Tworzenie rozwiązań programu SharePoint tworzy zestawy i plik pakietu rozwiązań (*wsp*). W poniższej tabeli przedstawiono lokalizacje tych plików podczas kompilacji.

|Kompiluj element|Folder wyjściowy|
|----------------|-------------------|
|Zestawy, bazy danych programu (*. pdb*) i pliki *. wsp* .|*\<ProjectName> \bin\debug* lub *\<ProjectName> \bin\Release*|
|Pliki elementów projektu programu SharePoint.|*\<ProjectName> \pkg\debug* lub *\<ProjectName> \pkg\release*|
|Kompiluj pliki pośrednie.|*\<ProjectName> \obj\debug* lub *\<ProjectName> \obj\release*|
|Pliki pośrednie pakietu.|*\<ProjectName> \pkgobj\debug* lub *\<ProjectName> \pkgobj\release*|

## <a name="build-sharepoint-solutions"></a>Tworzenie rozwiązań SharePoint
 Aby można było tworzyć rozwiązania programu SharePoint, na komputerze deweloperskim musi być zainstalowana poprawna wersja programu SharePoint Server. W przeciwnym razie Kompilowanie rozwiązań programu SharePoint jest takie samo jak w przypadku tworzenia innych typów projektów w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Aby uzyskać więcej informacji, zobacz [How to: build Solutions SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).

## <a name="debug-and-test-sharepoint-solutions"></a>Debugowanie i testowanie rozwiązań SharePoint
 Przed debugowaniem program [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] kopiuje pakiet *. wsp* do programu SharePoint Server, uaktywnia funkcje witryny i zakresu sieci Web, a w niektórych przypadkach uruchamia projekt. W innych przypadkach może być konieczne ręczne otworzenie projektu. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z rozwiązaniami programu SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) i [debugowaniem rozwiązań programu SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Debugowanie i weryfikowanie rozwiązań programu SharePoint przy użyciu funkcji Azure DevOps Services
 Azure DevOps Services funkcje takie jak testy jednostkowe i IntelliTrace umożliwiają dokładniejsze Lokalizowanie rozwiązań programu SharePoint. Profilowanie umożliwia lokalizowanie i identyfikowanie obszarów problemów z wydajnością w rozwiązaniach programu SharePoint. Aby uzyskać więcej informacji, zobacz [weryfikowanie i debugowanie kodu programu SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) i [profilowanie wydajności aplikacji programu SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).

## <a name="security-during-the-build-process"></a>Zabezpieczenia w procesie kompilacji
 Aby spakować lub wdrożyć rozwiązania programu SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] musi mieć uprawnienia do kopiowania plików na serwer programu SharePoint. Należy uruchomić program [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] jako proces z podwyższonym poziomem uprawnień, a konto użytkownika musi być administratorem zbioru witryn na serwerze programu SharePoint. Ponadto należy określić, czy projekt jest rozwiązaniem w trybie piaskownicy, czy też rozwiązaniem farmy. Aby uzyskać więcej informacji, zobacz [różnice między rozwiązaniami w trybie piaskownicy i farmą](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="using-the-clean-command"></a>Przy użyciu polecenia Clean
 Gdy na serwerze programu SharePoint jest zainstalowane rozwiązanie programu SharePoint do debugowania, polecenie **Oczyść** nie odinstaluje rozwiązania. Zamiast tego należy dezaktywować funkcje za pomocą konfiguracji programu SharePoint.

## <a name="see-also"></a>Zobacz także
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Przeglądanie połączeń programu SharePoint przy użyciu Eksplorator serwera](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
