---
title: Kompilowanie i debugowanie rozwiązań SharePoint | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: e91c1433fde85a9ec828a6a018bee986fdc7aa5c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62988138"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Kompilowanie i debugowanie rozwiązań SharePoint
  Ogólnie rzecz biorąc, kompilowania i debugowania rozwiązań programu SharePoint jest taka sama jak kompilowania i debugowania innych rodzajów projektów w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. W tematach w tej sekcji opisano różnice, które istnieją.

## <a name="project-output-for-sharepoint-solutions"></a>Dane wyjściowe projektu dla rozwiązań SharePoint
 Tworzenie rozwiązań programu SharePoint tworzy zestawów i pakietów rozwiązań (*.wsp*) pliku. W poniższej tabeli przedstawiono lokalizacje tych plików podczas kompilacji.

|Tworzenie elementu|Folder wyjściowy|
|----------------|-------------------|
|Zestaw, bazy danych programu (*.pdb*), a *.wsp* plików.|*\<Nazwa_projektu > \bin\debug* lub  *\<nazwa_projektu > \bin\release*|
|Plików elementów projektów programu SharePoint.|*\<Nazwa_projektu > \pkg\debug* lub  *\<nazwa_projektu > \pkg\release*|
|Pośrednie pliki kompilacji.|*\<Nazwa_projektu > \obj\debug* lub  *\<nazwa_projektu > \obj\release*|
|Pośrednie pliki pakietu.|*\<Nazwa_projektu > \pkgobj\debug* lub  *\<nazwa_projektu > \pkgobj\release*|

## <a name="build-sharepoint-solutions"></a>Kompilowanie rozwiązań SharePoint
 Aby utworzyć rozwiązanie programu SharePoint, na komputerze deweloperskim musi mieć poprawną wersję programu SharePoint server. W przeciwnym razie tworzenie rozwiązań programu SharePoint jest taka sama jak tworzenie innych rodzajów projektów w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [jak: Kompilowanie rozwiązań SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).

## <a name="debug-and-test-sharepoint-solutions"></a>Debugowanie i testowanie rozwiązań SharePoint
 Przed debugowaniem, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] kopie *.wsp* pakietu do serwera programu SharePoint włącza lokacji i funkcji należących do zakresu sieci Web, a w niektórych przypadkach uruchamia projektu. W innych przypadkach może być konieczne ręcznie otworzyć projekt. Aby uzyskać więcej informacji, zobacz [rozwiązań SharePoint Rozwiązywanie problemów z](../sharepoint/troubleshooting-sharepoint-solutions.md) i [rozwiązań SharePoint debugowania](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Debugowanie i sprawdź rozwiązań programu SharePoint przy użyciu funkcji usługom DevOps platformy Azure
 Funkcje usługom DevOps platformy Azure, jak testy jednostkowe i IntelliTrace pozwalają na więcej problemów dokładnie wyszukiwać w rozwiązaniach programu SharePoint. Profilowanie umożliwia znalezienie i zidentyfikowanie obszarów problemów wydajności w rozwiązaniach programu SharePoint. Aby uzyskać więcej informacji, zobacz [Weryfikowanie i debugowanie kodu programu SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) i [profilowanie wydajności aplikacji SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).

## <a name="security-during-the-build-process"></a>Zabezpieczenia w procesie kompilacji
 Do pakietu lub wdrażania rozwiązań programu SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] musi mieć uprawnienie do kopiowania plików do serwera programu SharePoint. Należy uruchomić [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] jako procesów z podwyższonym poziomem uprawnień i użytkownika konto musi być administratorem kolekcji witryn na serwerze programu SharePoint. Ponadto należy określić, czy projekt jest rozwiązanie w trybie piaskownicy lub farmy. Aby uzyskać więcej informacji, zobacz [różnice między piaskownicy oraz rozwiązaniami farmy](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="using-the-clean-command"></a>Za pomocą polecenia Wyczyść
 Rozwiązania programu SharePoint jest zainstalowany na serwerze programu SharePoint do debugowania, **czysty** polecenie nie powoduje odinstalowania rozwiązania. Zamiast tego należy dezaktywować funkcje za pośrednictwem konfiguracji programu SharePoint.

## <a name="see-also"></a>Zobacz także
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Przeglądanie połączeń SharePoint za pomocą Eksploratora serwera](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
