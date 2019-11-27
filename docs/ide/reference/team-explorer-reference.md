---
title: Dokumentacja wtyczki Team Explorer
ms.date: 12/04/2018
ms.topic: reference
ms.author: kaelli
author: KathrynEE
ms.manager: jillfra
ms.openlocfilehash: b1a956579b527de9df9d24bd09dda6ae48eff961
ms.sourcegitcommit: 08105865a9643fb20dce9b8b7580452cfbbe7ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2019
ms.locfileid: "74538575"
---
# <a name="team-explorer-reference"></a>Dokumentacja wtyczki Team Explorer

Ten artykuł zawiera linki do artykułów DevOps platformy Azure dotyczących różnych funkcji w programie **Team Explorer**.

Użyj okna narzędzia **Team Explorer** , aby koordynować wysiłki kodu z innymi członkami zespołu, aby opracować projekt i zarządzać pracą przypisaną do Ciebie, Twojego zespołu lub Twoich projektów. **Team Explorer** łączy program Visual Studio z repozytoriami git i GitHub, repozytoriami wersji Team Foundation Version Control (TFVC) i projektami obsługiwanymi w [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) lub [Azure DevOps Server](/azure/devops/index-all) lokalnymi (wcześniej znanym jako TFS). Możesz zarządzać kodem źródłowym, elementami roboczymi i kompilacjami.

## <a name="home-page"></a>Strona główna

Po [nawiązaniu połączenia z projektem](../connect-team-project.md) w **Team Explorer**następujące linki staną się dostępne w sekcji **projektu** :

- [Klonowanie repozytorium](/azure/devops/repos/git/clone)
- [Portal sieci Web](/azure/devops/project/navigation/index)
- [Tablica zadań](/azure/devops/boards/sprints/task-board)

Strona **główna** ma różne funkcje w zależności od tego, czy masz połączenie z repozytorium [git](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio) czy [Kontrola wersji serwera Team Foundation (TFVC)](/azure/devops/repos/tfvc/overview) .

> [!TIP]
> Aby porównać dwa systemy kontroli wersji, zobacz [Wybieranie odpowiedniej kontroli wersji dla projektu (Azure DevOps)](/azure/devops/repos/tfvc/comparison-git-tfvc).

| Strona **główna** z usługą git | Strona **główna** z TFVC |
| - | - |
| ![Strona główna Team Explorer z usługą Git w programie Visual Studio 2019](media/team-explorer-reference/team-explorer-git.png) | ![Strona główna Team Explorer z TFVC w programie Visual Studio](media/team-explorer-reference/team-explorer-tfvc.png) |

## <a name="changes-page-git"></a>Strona zmiany (Git)

Zobacz [zapisywanie pracy z zatwierdzeniami](/azure/devops/repos/git/commits).

## <a name="branches-page-git"></a>Strona gałęzi (Git)

Zobacz [Tworzenie pracy w gałęziach](/azure/devops/repos/git/branches).

## <a name="pull-requests-page-git"></a>Strona żądania ściągnięcia (Git)

Zobacz sekcję [Przegląd kodu z żądaniami ściągnięcia](/azure/devops/repos/git/pullrequest).

## <a name="sync-page-git"></a>Strona synchronizacji (Git)

Zobacz [Aktualizacja kodu za pomocą pobierania i ściągania](/azure/devops/repos/git/pulling).

## <a name="tags-page-git"></a>Strona tagów (Git)

Zobacz artykuł [Pracuj z tagami usługi git](/azure/devops/repos/git/git-tags).

## <a name="my-work-page-tfvc"></a>Strona Moja służbowa (TFVC)

Zobacz [zadania zawieszania/wznawiania](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) oraz [Przegląd kodu](/azure/devops/repos/tfvc/day-life-alm-developer-suspend-work-fix-bug-conduct-code-review).

## <a name="pending-changes-page-tfvc"></a>Strona oczekujące zmiany (TFVC)

Zobacz [zarządzanie oczekującymi zmianami](/azure/devops/repos/tfvc/develop-code-manage-pending-changes), [Znajdowanie zestawów odłożonych](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets)i [Rozwiązywanie konfliktów](/azure/devops/repos/tfvc/resolve-team-foundation-version-control-conflicts).

## <a name="source-control-explorer-page-tfvc"></a>Strona Eksploator kontroli źródła (TFVC)

Zobacz [Dodawanie/wyświetlanie plików i folderów](/azure/devops/repos/tfvc/add-files-server).

## <a name="work-items-page"></a>Strona elementów roboczych

Strona **elementy robocze** pozwala zobaczyć zapytania o elementy [robocze](/azure/devops/boards/work-items/about-work-items) . Zobacz:

- [Dodaj elementy robocze](/azure/devops/boards/backlogs/add-work-items)
- [Użyj edytora zapytań, aby wyświetlić listę zapytań i zarządzać nimi](/azure/devops/boards/queries/using-queries)
- [Organizuj foldery zapytań i Ustaw uprawnienia do zapytań](/azure/devops/boards/queries/set-query-permissions)
- [Otwórz zapytanie w programie Excel](/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel)
- [Otwórz zapytanie w projekcie](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)
- [Lista wyników zapytania e-mail przy użyciu programu Outlook](/azure/devops/boards/queries/share-plans)
- [Tworzenie raportów z kwerendy w programie Excel](/azure/devops/report/excel/create-status-and-trend-excel-reports) (tylko TFS)

::: moniker range=">= vs-2019"

> [!NOTE]
> W programie Visual Studio 2019 istnieje nowe [środowisko elementów roboczych](/azure/devops/boards/work-items/set-work-item-experience-vs) . Aby uzyskać informacje o wyświetlaniu elementów roboczych w programie Visual Studio 2019, zobacz [Wyświetlanie i Dodawanie elementów roboczych](/azure/devops/boards/work-items/view-add-work-items).

::: moniker-end

## <a name="builds-page"></a>Strona kompilacje

Strona **kompilacje** umożliwia wyświetlenie definicji kompilacji dla projektu.

Zobacz:

- [Tworzenie potoków kompilacji](/azure/devops/pipelines/tasks/index)
- [Wyświetl kompilacje i zarządzaj nimi](/azure/devops/pipelines/overview)
- [Zarządzanie kolejką kompilacji](/azure/devops/pipelines/agents/pools-queues)
- [Instalowanie narzędzi ciągłego dostarczania (CD) dla programu Visual Studio](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#install-continuous-delivery-cd-tools-for-visual-studio-2017)
- [Konfigurowanie i wykonywanie ciągłego dostarczania dla aplikacji](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#configure-and-execute-continuous-delivery-cd-for-your-app)

## <a name="settings-page"></a>Strona Ustawienia

Strona **Ustawienia** umożliwia skonfigurowanie funkcji administracyjnych dla projektu lub kolekcji projektów. Zobacz następujące artykuły:

| {1&gt;Projekt&lt;1} | Kolekcja projektów | Inne |
| - | - | - |
| [Zabezpieczenia, członkostwo w grupie](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Zabezpieczenia, kontrola źródła (TFVC)](/azure/devops/organizations/security/set-git-tfvc-repository-permissions)<br/>[Obszary elementu pracy](/azure/devops/organizations/settings/set-area-paths)<br/>[Iteracje elementu pracy](/azure/devops/organizations/settings/set-iteration-paths-sprints)<br/>[Ustawienia portalu](/azure/devops/report/sharepoint-dashboards/configure-or-add-a-project-portal)<br/>[Alerty projektu](/azure/devops/notifications/howto-manage-team-notifications) | [Zabezpieczenia, członkostwo w grupie](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Kontrola źródła (TFVC)](/azure/devops/repos/tfvc/decide-between-using-local-server-workspace)<br/>[Menedżer szablonu procesu](/azure/devops/boards/work-items/guidance/manage-process-templates) | [Ustawienia globalne git](/azure/devops/repos/git/git-config)<br/>[Ustawienia repozytorium git](/azure/devops/repos/git/git-config) |

## <a name="see-also"></a>Zobacz także

- [Nawiązywanie połączenia z projektami w Team Explorer](../../ide/connect-team-project.md)