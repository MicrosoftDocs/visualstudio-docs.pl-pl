---
layout: LandingPage
title: Kontrola wersji
description: Przewodnik Wprowadzenie do kontroli wersji w programie Visual Studio
keywords: VSTS, TFS, Version Control
author: steved0x
ms.manager: jillfra
ms.author: sdanie
ms.date: 12/15/2017
ms.topic: landing-page
ms.prod: .net-core
ms.assetid: 2c119a5f-0272-48c0-8d6c-806196944aea
ms.workload:
- multiple
ms.openlocfilehash: 97facaed877030dca4a6a2257147c4d92201ab55
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58322707"
---
# <a name="version-control-in-visual-studio"></a>Kontrola wersji w programie Visual Studio

Systemy kontroli wersji pomogły Ci śledzić zmiany w kodzie wraz z upływem czasu. Po wprowadzeniu dowolnych zmian, system kontroli wersji wykonuje migawkę plików. System kontroli wersji trwale zapisuje tej migawki, dzięki czemu użytkownik może ją później przywrócić Jeśli jest potrzebna. Program Visual Studio udostępnia [Git](/azure/devops/repos/git/index?view=vsts) i [Team Foundation Version Control (TFVC)](/azure/devops/repos/tfvc/index?view=vsts). Aby wybrać między dwoma systemami, zobacz [Wybieranie właściwej kontroli wersji dla projektu](/azure/devops/repos/tfvc/comparison-git-tfvc?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json).

## <a name="git"></a>Git

Git to obecnie najczęściej używany system kontroli wersji i szybko staje się standardem kontroli wersji. Git to Rozproszony system kontroli wersji, co oznacza, że Twoja lokalna kopia kodu jest kompletną wersją repozytorium kontroli. Upewnij te w pełni funkcjonalne repozytoria lokalne ułatwiają pracę w trybie offline lub zdalnie. Pracę zatwierdzasz lokalnie, a następnie synchronizujesz swoją kopię repozytorium z kopią na serwerze. Taki wzorzec pracy różni się od scentralizowanej kontroli wersji której klient musi synchronizować kod z serwerem przed utworzeniem nowych wersji kodu.

<!-- markdownlint-disable MD033 -->
<ul class="panelContent cardsFTitle">
    <li>
        <a href="/azure/devops/git/what-is-git">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Poznaj usługę Git</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/git/share-your-code-in-git-vs-2017">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Rozpoczynanie pracy z usługą Git w programie Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/git/clone">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Klonowanie istniejącego repozytorium Git</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>

## <a name="tfvc"></a>TFVC

Team Foundation Version Control (TFVC) to scentralizowany system kontroli wersji. Zazwyczaj członkowie zespołu mają tylko jedną wersję każdego pliku na swoich komputerach deweloperskich. Dane historyczne są utrzymywane tylko na serwerze. Gałęzie bazują na ścieżkach i są tworzone na serwerze.

<ul class="panelContent cardsFTitle">
    <li>
        <a href="/azure/devops/repos/tfvc/overview">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Dowiedz się, TFVC</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Rozpoczynanie pracy z użyciem systemu TFVC w programie Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
   <li>
        <a href="/azure/devops/repos/tfvc/get-code-reviewed-vs">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Przegląd kodu</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>

## <a name="resources"></a>Zasoby

- [Podręcznik usługi Git Pro](https://git-scm.com/book/en/v2)
- [Planowanie migracji do usługi Git](https://docs.microsoft.com/azure/devops/git/centralized-to-git)
- [Migrowanie z TFVC do usługi Git](https://docs.microsoft.com/azure/devops/git/migrate-from-tfvc-to-git)
- [Kontrola wersji (Visual Studio dla komputerów Mac)](/visualstudio/mac/version-control)