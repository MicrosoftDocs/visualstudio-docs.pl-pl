---
title: Słownik wtyczki kontroli źródła | Microsoft Docs
description: Ten artykuł zawiera przydatne warunki i definicje, które odnoszą się do dokumentacji zestawu SDK dodatku do kontroli źródła.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5fe262091b25db3dae0388427afc3af6c9027872
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090099"
---
# <a name="source-control-plug-in-glossary"></a>Słownik wtyczki kontroli źródła
Poniższe pomocne warunki i definicje odnoszą się do dokumentacji zestawu SDK dodatku do kontroli źródła.

## <a name="definitions"></a>Definicje
 Ewidencjonowanie, gdy użytkownik wprowadza zmiany w roboczej kopii, użytkownik musi wysłać zmiany z kopii roboczej do centralnego repozytorium kontroli źródła. Spowoduje to utworzenie nowej wersji pliku, który jest dostępny dla innych użytkowników. Ten proces jest nazywany zaewidencjonowaniam.

 Wyewidencjonuj czynność żądania kopii roboczej z repozytorium, informując repozytorium, aby go zmodyfikować. Kopia robocza odzwierciedla stan projektu od momentu wyewidencjonowania.

 Klient programu, który korzysta z systemu kontroli kodu źródłowego. Na potrzeby tej dokumentacji jest to środowisko IDE programu Visual Studio.

 Dodaj komentarz do komunikatu opisującego zmiany, które użytkownik może dołączyć do poprawki w przypadku wykonania operacji kontroli źródła.

 Konflikt sytuacji, gdy dwaj użytkownicy próbują zaewidencjonować zmiany w tym samym regionie tego samego pliku. Zwykle należy wykonać scalanie.

 Katalog folder lokalny po stronie klienta jest określany jako katalog. Jest to kopia, w której użytkownik wprowadza zmiany. Może istnieć wiele kopii roboczych danego projektu; Ogólnie każdy deweloper ma własną kopię.

 Pobieranie operacji get powoduje, że kopia robocza użytkownika jest aktualna przy użyciu kopii repozytorium. W przeciwieństwie do wyewidencjonowania, pobieranie jest wykonywane, gdy użytkownik po prostu potrzebuje najnowszej kopii, ale nie wprowadza żadnych zmian.

 Historia jest zazwyczaj podsumowaniem wszystkich wyewidencjonowania, zaewidencjonowania, aktualizacji, tagów i wydań wykonanych w repozytorium kontroli źródła.

 IDE ogólnie dotyczy zintegrowanego środowiska projektowego programu Visual Studio. Jednak może ona również odnosić się do innych środowisk klienckich, które uznają interfejs API wtyczki kontroli źródła.

 Scal proces, w którym są łączone co najmniej dwa pliki kodu źródłowego, aby utworzyć nowy plik, który zawiera wszystkie funkcje z poprzednich plików. Koncepcja ta jest istotna w kontroli wersji, w której co najmniej dwaj deweloperzy pracują nad plikami jednocześnie.

 Projekt folder kontroli źródła jest często określany jako projekt. Nie ma żadnych relacji z projektami ani rozwiązaniami w programie Visual Studio.

 Wtyczka biblioteki DLL, która zapewnia funkcje kontroli źródła przez implementację interfejsu API wtyczki kontroli źródła.

 Repozytorium kopii głównej, w której system kontroli źródła przechowuje pełną historię poprawek projektu. Każdy projekt ma dokładnie jedno repozytorium.

 Poprawka zatwierdzonej zmiany w historii pliku lub zestawu plików. Poprawka jest jedną migawką w stale zmienianym projekcie.

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
