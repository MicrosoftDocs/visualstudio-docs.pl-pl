---
title: Słownik wtyczki kontroli kodu źródłowego | Microsoft Docs
description: Ten artykuł zawiera przydatne terminy i definicje dotyczące dokumentacji zestawu SDK wtyczki kontroli kodu źródłowego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 05b215de4191362a539d3b03ac858da6bb7ee292
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899527"
---
# <a name="source-control-plug-in-glossary"></a>Słownik wtyczki kontroli źródła
Następujące przydatne terminy i definicje odnoszą się do dokumentacji zestawu SDK wtyczki kontroli kodu źródłowego.

## <a name="definitions"></a>Definicje
 Ewidencja Gdy użytkownik wprowadza zmiany w kopii roboczej, użytkownik musi wysłać zmiany z kopii roboczej do centralnego repozytorium kontroli źródła. Powoduje to utworzenie nowej wersji pliku, która jest dostępna dla innych użytkowników. Ten proces jest nazywany zaewidencją.

 Checkout (Wyewidencjonowanie) Żądanie kopii roboczej z repozytorium i poinformowanie repozytorium o zamiarze jego zmodyfikowania. Kopia robocza odzwierciedla stan projektu od momentu jego wyewidencjonowania.

 Klient program, który używa systemu kontroli kodu źródłowego. Na potrzeby tej dokumentacji jest to Visual Studio IDE.

 Komentarz Komunikat opisujący zmiany, które użytkownik może dołączyć do poprawki podczas operacji kontroli źródła.

 Konflikt Sytuacja, w której dwóch użytkowników próbuje zaewidencjonić zmiany w tym samym regionie tego samego pliku. Zwykle należy wykonać scalanie.

 Katalog Lokalny folder po stronie klienta jest określany jako katalog. Jest to kopia, w której użytkownik faktycznie wprowadza zmiany. Może być wiele kopii roboczych danego projektu; Zazwyczaj każdy deweloper ma własną kopię.

 Get A get operation brings the working copy up to date with the repository copy .Get A get operation brings the working copy to the user's working copy with the repository copy. W przeciwieństwie do wyewidencjonowania, pobranie jest wykonywane, gdy użytkownik po prostu potrzebuje najnowszej kopii, ale nie zamierza wprowadzać żadnych zmian.

 Historia Jest to zwykle podsumowanie wszystkich wyewidencjonowań, zaewidencjonowań, aktualizacji, tagów i wydań w repozytorium kontroli źródła.

 Środowisko IDE ogólnie odnosi się do Visual Studio zintegrowanego środowiska projektowego. Może jednak również odwoływać się do innych środowisk klienckich, które rozpoznają interfejs API wtyczki kontroli kodu źródłowego.

 Scal proces, w którym co najmniej dwa pliki kodu źródłowego są łączone w celu tworzenia nowego pliku, który zawiera wszystkie funkcje z poprzednich plików. Ta koncepcja jest istotna w przypadku kontroli wersji, w której co najmniej dwóch deweloperów pracuje nad plikami jednocześnie.

 Projekt Folder kontroli źródła jest często określany jako projekt. Nie ma to żadnej relacji z projektami ani rozwiązaniami w Visual Studio.

 Wtyczka biblioteki DLL, która zapewnia funkcje kontroli źródła przez zaimplementowanie interfejsu API wtyczki kontroli kodu źródłowego.

 Repozytorium Kopia główna, w której system kontroli źródła przechowuje pełną historię poprawek projektu. Każdy projekt ma dokładnie jedno repozytorium.

 Poprawka Zatwierdzona zmiana w historii pliku lub zestawu plików. Poprawka to jedna migawka w ciągle zmieniającym się projekcie.

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
