---
title: Dokumentacja programu Team Explorer
ms.date: 12/04/2018
ms.prod: visual-studio-dev15
ms.topic: reference
ms.author: kaelli
author: KathrynEE
ms.manager: douge
ms.openlocfilehash: 2b4ab4677e8fe8fec9f1915d79cbcf841787cb48
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834170"
---
# <a name="team-explorer-reference"></a>Dokumentacja programu Team Explorer

Ten artykuł zawiera linki do artykułów DevOps platformy Azure na temat różnych funkcji w **Team Explorer**.

Użyj **Team Explorer** okna narzędzi do koordynowania swoich działań kodu z innymi członkami zespołu, aby opracować projekt, a także do zarządzania pracą, która jest przypisana do Ciebie, Twojego zespołu lub projektów. **Team Explorer** łączy program Visual Studio z repozytoriów Git i GitHub, repozytoriów kontroli (TFVC) w wersji Team Foundation i projektów w serwisie [usługom DevOps platformy Azure](/azure/devops/user-guide/what-is-azure-devops-services) lub lokalną [platformy Azure Serwer DevOps](/tfs/index) (wcześniej znane jako serwera TFS). Można zarządzać kodem źródłowym, elementami roboczymi i kompilacjami.

## <a name="home-page"></a>Strona główna

Po zakończeniu [Połącz z projektem](../connect-team-project.md) w **Team Explorer**, poniższe łącza stają się dostępne w **projektu** sekcji:

- [Klonuj repozytorium](/azure/devops/repos/git/clone)
- [Portal sieci Web](/azure/devops/project/navigation/index)
- [Tablica zadań](/azure/devops/boards/sprints/task-board)

**Home** strona zawiera różne funkcje, w zależności od tego, czy nawiązano połączenie [Git](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio) lub [Team Foundation Version Control (TFVC)](/azure/devops/repos/tfvc/overview) repozytorium.

> [!TIP]
> Dla porównania systemów kontroli dwóch wersji, zobacz [Wybieranie właściwej kontroli wersji dla projektu (DevOps platformy Azure)](/azure/devops/repos/tfvc/comparison-git-tfvc).

| **Strona główna** strony za pomocą narzędzia Git | **Strona główna** strony z użyciem systemu TFVC |
| - | - |
| ![Strony głównej programu Team Explorer przy użyciu narzędzia Git w programie Visual Studio 2019 r.](media/team-explorer-reference/team-explorer-git.png) | ![Strony głównej programu Team Explorer z użyciem systemu TFVC w programie Visual Studio 2017](media/team-explorer-reference/team-explorer-tfvc.png) |

## <a name="changes-page-git"></a>Strony zmiany (Git)

Zobacz [zapisywanie pracy z zatwierdzeniami](/azure/devops/repos/git/commits).

## <a name="branches-page-git"></a>Strony gałęzi (Git)

Zobacz [tworzenie zadań w gałęziach](/azure/devops/repos/git/branches).

## <a name="pull-requests-page-git"></a>Strony żądania ściągnięcia (Git)

Zobacz [przeglądanie kodu za pomocą żądań ściągnięcia](/azure/devops/repos/git/pullrequest).

## <a name="sync-page-git"></a>Strony synchronizacji (Git)

Zobacz [aktualizowanie kodu za pomocą pobierania i ściągania](/azure/devops/repos/git/pulling).

## <a name="tags-page-git"></a>Strona tagi (Git)

Zobacz [pracować z tagów usługi Git](/azure/devops/repos/git/git-tags).

## <a name="my-work-page-tfvc"></a>Strony Moja praca (TFVC)

Zobacz [pracy wstrzymań/wznowień](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) i [Przegląd kodu](/azure/devops/repos/tfvc/day-life-alm-developer-suspend-work-fix-bug-conduct-code-review).

## <a name="pending-changes-page-tfvc"></a>Strony oczekujących zmian (TFVC)

Zobacz [Zarządzaj oczekującymi zmianami](/azure/devops/repos/tfvc/develop-code-manage-pending-changes), [Znajdź zestaw na półce](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets), i [Rozwiązywanie konfliktów](/azure/devops/repos/tfvc/resolve-team-foundation-version-control-conflicts).

## <a name="source-control-explorer-page-tfvc"></a>Strona Eksploratora kontroli źródła (TFVC)

Zobacz [Add/Wyświetl pliki i foldery](/azure/devops/repos/tfvc/add-files-server).

## <a name="work-items-page"></a>Strona elementów roboczych

**Elementy robocze** strona pozwala zobaczyć [elementu roboczego](/azure/devops/boards/work-items/about-work-items) zapytania. Zobacz:

- [Dodawanie elementów roboczych](/azure/devops/boards/backlogs/add-work-items)
- [Używanie edytora zapytań do listy i zarządzać zapytaniami](/azure/devops/boards/queries/using-queries)
- [Organizowanie folderów zapytań i ustawianie uprawnień zapytań](/azure/devops/boards/queries/set-query-permissions)
- [Otwórz zapytanie w programie Excel](/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel)
- [Otwórz zapytanie w projekcie](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)
- [Lista wyników zapytania poczty e-mail przy użyciu programu Outlook](/azure/devops/boards/queries/share-plans)
- [Tworzenie raportów na podstawie zapytania w programie Excel](/azure/devops/report/excel/create-status-and-trend-excel-reports) (tylko w programie TFS)

::: moniker range=">= vs-2019"

> [!NOTE]
> Jest dostępny nowy [środowisko elementów roboczych](/azure/devops/boards/work-items/set-work-item-experience-vs) w programie Visual Studio 1 2019 r w wersji zapoznawczej. Informacje o wyświetlaniu elementów roboczych w programie Visual Studio 2019 r w wersji zapoznawczej 1, zobacz [widoku i dodać elementy robocze](/azure/devops/boards/work-items/view-add-work-items).

::: moniker-end

## <a name="builds-page"></a>Strona kompilacji

**Kompilacje** strona umożliwia sprawdzenie, definicji kompilacji dla projektu.

Zobacz:

- [Twórz potoki kompilacji](/azure/devops/pipelines/tasks/index)
- [Przeglądaj i Zarządzaj kompilacjami](/azure/devops/pipelines/overview)
- [Zarządzaj kolejką kompilacji](/azure/devops/pipelines/agents/pools-queues)
- [Instalowanie narzędzi ciągłe dostarczanie (CD) dla programu Visual Studio](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#install-continuous-delivery-cd-tools-for-visual-studio-2017)
- [Konfigurowanie i wykonywanie ciągłe dostarczanie (CD) aplikacji](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#configure-and-execute-continuous-delivery-cd-for-your-app)

## <a name="settings-page"></a>Strona Ustawienia

**Ustawienia** strona umożliwia skonfigurowanie funkcji administracyjnych dla projektu lub kolekcji projektów. Zobacz następujące artykuły:

| Projekt | Kolekcja projektów | Inne |
| - | - | - |
| [Zabezpieczeń, członkostwa w grupie](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Zabezpieczenia, kontroli źródła (TFVC)](/azure/devops/organizations/security/set-git-tfvc-repository-permissions)<br/>[Obszary elementu roboczego](/azure/devops/organizations/settings/set-area-paths)<br/>[Iteracje elementu roboczego](/azure/devops/organizations/settings/set-iteration-paths-sprints)<br/>[Ustawienia portalu](/azure/devops/report/sharepoint-dashboards/configure-or-add-a-project-portal)<br/>[Alerty projektu](/azure/devops/notifications/howto-manage-team-notifications) | [Zabezpieczeń, członkostwa w grupie](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Kontroli źródła (TFVC)](/azure/devops/repos/tfvc/decide-between-using-local-server-workspace)<br/>[Menedżer szablonów procesu](/azure/devops/boards/work-items/guidance/manage-process-templates) | [Ustawienia globalne Git](/azure/devops/repos/git/git-config)<br/>[Ustawienia repozytorium Git](/azure/devops/repos/git/git-config) |

## <a name="see-also"></a>Zobacz także

- [Połącz się z projektami w programie Team Explorer](../../ide/connect-team-project.md)