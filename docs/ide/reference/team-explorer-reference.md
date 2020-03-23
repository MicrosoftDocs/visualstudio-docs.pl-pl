---
title: Dokumentacja wtyczki Team Explorer
ms.date: 12/04/2018
ms.topic: reference
ms.author: kaelli
author: KathrynEE
ms.manager: jillfra
ms.openlocfilehash: b1a956579b527de9df9d24bd09dda6ae48eff961
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74538575"
---
# <a name="team-explorer-reference"></a>Dokumentacja wtyczki Team Explorer

Ten artykuł zawiera łącza do artykułów programu Azure DevOps dotyczących różnych funkcji w **Eksploratorze zespołu.**

Okno narzędzia **Eksplorator zespołu** służy do koordynowania wysiłków związanych z kodem z innymi członkami zespołu w celu opracowania projektu i zarządzania pracą przypisaną do Ciebie, zespołu lub projektów. **Team Explorer** łączy program Visual Studio z repozytoriami Git i GitHub, repozytoriami kontroli wersji programu Team Foundation (TFVC) oraz projektami hostowanymi w [usługach Azure DevOps](/azure/devops/user-guide/what-is-azure-devops-services) lub lokalnym serwerze Azure [DevOps Server](/azure/devops/index-all) (wcześniej znanym jako TFS). Można zarządzać kodem źródłowym, elementami roboczymi i kompilacjami.

## <a name="home-page"></a>Strona główna

Po [nawiązaniu połączenia z projektem](../connect-team-project.md) w **Eksploratorze zespołu**następujące łącza stają się dostępne w sekcji **Projekt:**

- [Repozytorium klonowania](/azure/devops/repos/git/clone)
- [Portal internetowy](/azure/devops/project/navigation/index)
- [Komisja zadań](/azure/devops/boards/sprints/task-board)

Strona **główna** ma różne funkcje w zależności od tego, czy masz połączenie z repozytorium [TFVC](/azure/devops/repos/tfvc/overview) [(Git](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio) lub Team Foundation Version Control).

> [!TIP]
> Aby porównać dwa systemy kontroli wersji, zobacz [Wybieranie odpowiedniej kontroli wersji dla projektu (Azure DevOps)](/azure/devops/repos/tfvc/comparison-git-tfvc).

| Strona **główna** z Git | Strona **główna** z TFVC |
| - | - |
| ![Strona główna eksploratora zespołu z git w programie Visual Studio 2019](media/team-explorer-reference/team-explorer-git.png) | ![Strona główna Eksploratora zespołu z TFVC w programie Visual Studio](media/team-explorer-reference/team-explorer-tfvc.png) |

## <a name="changes-page-git"></a>Strona Zmiany (Git)

Zobacz [Zapisywanie pracy z zatwierdzeń](/azure/devops/repos/git/commits).

## <a name="branches-page-git"></a>Strona Gałęzie (Git)

Zobacz [Tworzenie pracy w oddziałach](/azure/devops/repos/git/branches).

## <a name="pull-requests-page-git"></a>Strona Żądania ściągnięcia (Git)

Zobacz [Przeglądanie kodu z żądaniami ściągnięcia](/azure/devops/repos/git/pullrequest).

## <a name="sync-page-git"></a>Strona synchronizacji (Git)

Zobacz [Aktualizowanie kodu za pomocą funkcji pobierania i ściągania](/azure/devops/repos/git/pulling).

## <a name="tags-page-git"></a>Strona tagów (Git)

Zobacz [Praca z tagami Git](/azure/devops/repos/git/git-tags).

## <a name="my-work-page-tfvc"></a>Strona Moja praca (TFVC)

Zobacz [Wstrzymanie/wznowienie pracy](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) i [przegląd kodu](/azure/devops/repos/tfvc/day-life-alm-developer-suspend-work-fix-bug-conduct-code-review).

## <a name="pending-changes-page-tfvc"></a>Strona Oczekujące zmiany (TFVC)

Zobacz [Zarządzanie oczekującymi zmianami](/azure/devops/repos/tfvc/develop-code-manage-pending-changes), [Znajdowanie sześcienne](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets)i [Rozwiązywanie konfliktów](/azure/devops/repos/tfvc/resolve-team-foundation-version-control-conflicts).

## <a name="source-control-explorer-page-tfvc"></a>Strona Eksploratora kontroli źródła (TFVC)

Zobacz [Dodawanie/wyświetlanie plików i folderów](/azure/devops/repos/tfvc/add-files-server).

## <a name="work-items-page"></a>Strona Elementy robocze

Elementy **robocze** strona umożliwia wyświetlanie kwerend [elementów roboczych.](/azure/devops/boards/work-items/about-work-items) Zobacz:

- [Dodawanie elementów roboczych](/azure/devops/boards/backlogs/add-work-items)
- [Używanie edytora zapytań do wystawiania zapytań i zarządzania nimi](/azure/devops/boards/queries/using-queries)
- [Organizowanie folderów kwerend i ustawianie uprawnień kwerend](/azure/devops/boards/queries/set-query-permissions)
- [Otwieranie kwerendy w programie Excel](/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel)
- [Otwórz kwerendę w programie Project](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)
- [Lista wyników kwerendy e-mail przy użyciu programu Outlook](/azure/devops/boards/queries/share-plans)
- [Tworzenie raportów z kwerendy w programie Excel](/azure/devops/report/excel/create-status-and-trend-excel-reports) (tylko TFS)

::: moniker range=">= vs-2019"

> [!NOTE]
> W programie Visual Studio 2019 pojawiło się nowe [środowisko elementów roboczych.](/azure/devops/boards/work-items/set-work-item-experience-vs) Aby uzyskać informacje dotyczące wyświetlania elementów pracy w programie Visual Studio 2019, zobacz [Wyświetlanie i dodawanie elementów roboczych](/azure/devops/boards/work-items/view-add-work-items).

::: moniker-end

## <a name="builds-page"></a>Strona Kompilacje

Buduje **Builds** strona umożliwia wyświetlanie definicji kompilacji dla projektu.

Zobacz:

- [Tworzenie potoków kompilacji](/azure/devops/pipelines/tasks/index)
- [Wyświetlanie kompilacji i zarządzanie nimi](/azure/devops/pipelines/overview)
- [Zarządzanie kolejką kompilacji](/azure/devops/pipelines/agents/pools-queues)
- [Instalowanie narzędzi ciągłego dostarczania (CD) dla programu Visual Studio](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#install-continuous-delivery-cd-tools-for-visual-studio-2017)
- [Konfigurowanie i wykonywanie ciągłego dostarczania (CD) dla aplikacji](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#configure-and-execute-continuous-delivery-cd-for-your-app)

## <a name="settings-page"></a>Strona Ustawienia

Strona **Ustawienia** umożliwia skonfigurowanie funkcji administracyjnych dla kolekcji projektu lub projektu. Zobacz następujące artykuły:

| Project | Kolekcja projektów | Inne |
| - | - | - |
| [Bezpieczeństwo, członkostwo w grupie](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Bezpieczeństwo, kontrola źródła (TFVC)](/azure/devops/organizations/security/set-git-tfvc-repository-permissions)<br/>[Obszary elementów roboczych](/azure/devops/organizations/settings/set-area-paths)<br/>[Iteracje elementu roboczego](/azure/devops/organizations/settings/set-iteration-paths-sprints)<br/>[Ustawienia portalu](/azure/devops/report/sharepoint-dashboards/configure-or-add-a-project-portal)<br/>[Alerty dotyczące projektu](/azure/devops/notifications/howto-manage-team-notifications) | [Bezpieczeństwo, członkostwo w grupie](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Kontrola źródła (TFVC)](/azure/devops/repos/tfvc/decide-between-using-local-server-workspace)<br/>[Menedżer szablonów procesów](/azure/devops/boards/work-items/guidance/manage-process-templates) | [Ustawienia globalne git](/azure/devops/repos/git/git-config)<br/>[Ustawienia repozytorium Git](/azure/devops/repos/git/git-config) |

## <a name="see-also"></a>Zobacz też

- [Łączenie się z projektami w Eksploratorze zespołu](../../ide/connect-team-project.md)