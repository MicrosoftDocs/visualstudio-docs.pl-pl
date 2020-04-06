---
title: Słowniczek wtyczki source control | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3835561eb63fa2a4a71174732c07ecd73f1df5d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699910"
---
# <a name="source-control-plug-in-glossary"></a>Słownik wtyczki kontroli źródła
Poniższe przydatne terminy i definicje odnoszą się do dokumentacji SDK wtyczki source control.

## <a name="definitions"></a>Definicje
 Zaewidencjonuj Gdy użytkownik wprowadza zmiany w kopii roboczej, użytkownik musi wysłać zmiany z kopii roboczej do centralnego repozytorium kontroli źródła. Spowoduje to utworzenie nowej wersji pliku, która jest dostępna dla innych użytkowników. Proces ten jest nazywany odprawą.

 Wyewidencjonuj Czynność żądania kopii roboczej z repozytorium, informując repozytorium o zamiarze jej modyfikacji. Kopia robocza odzwierciedla stan projektu w momencie wyewidencjonowania.

 Klient Program, który używa systemu kontroli kodu źródłowego. Na potrzeby tej dokumentacji jest to ide programu Visual Studio.

 Komentarz Komunikat opisujący zmiany, które użytkownik może dołączyć do poprawki podczas wykonywania operacji kontroli źródła.

 Konflikt Sytuacja, gdy dwóch użytkowników próbuje zaewidencjonować zmiany w tym samym regionie tego samego pliku. Zazwyczaj należy wykonać scalanie.

 Katalog Folder lokalny po stronie klienta jest określany jako katalog. Jest to kopia, w której użytkownik faktycznie wprowadza zmiany. Może istnieć wiele kopii roboczych danego projektu; zazwyczaj każdy deweloper ma własną kopię.

 Operacja Get A get aktualizuje kopię roboczą użytkownika za pomocą kopii repozytorium. W przeciwieństwie do wyewidencjonowania, get jest wykonywane, gdy użytkownik po prostu potrzebuje najnowszej kopii, ale zamierza wprowadzić żadnych zmian.

 Historia Jest to zazwyczaj podsumowanie wszystkich wyewidencjonowania, zaewidencjonowania, aktualizacji, tagów i wydań wykonanych w repozytorium kontroli źródła.

 IDE ogólnie odwołuje się do visual studio zintegrowane środowisko programistyczne. Jednak może również odwoływać się do innych środowisk klienta, które rozpoznają interfejs API wtyczki kontroli źródła.

 Scalanie procesu, podczas którego dwa lub więcej plików kodu źródłowego są łączone w celu utworzenia nowego pliku, który zawiera wszystkie funkcje z poprzednich plików. Ta koncepcja jest niezbędna w kontroli wersji, gdzie dwóch lub więcej programistów pracuje nad plikami jednocześnie.

 Projekt Folder kontroli źródła jest często określany jako projekt. Nie ma żadnych relacji z projektami lub rozwiązaniami w programie Visual Studio.

 Biblioteka DLL dodatku Plug-in, która zapewnia funkcję kontroli źródła przez implementowanie interfejsu API wtyczki kontroli źródła.

 Repozytorium Kopia główna, w której system kontroli źródła przechowuje pełną historię wersji projektu. Każdy projekt ma dokładnie jedno repozytorium.

 Wersja Zatwierdzona zmiana w historii pliku lub zestawu plików. Wersja to jedna migawka w stale zmieniającym się projekcie.

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
