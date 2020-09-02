---
title: Słownik wtyczki kontroli źródła | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f5120a5c6678cac32ef65e08ef7dc34649364cf9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160603"
---
# <a name="source-control-plug-in-glossary"></a>Słownik wtyczki kontroli źródła
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poniższe pomocne warunki i definicje odnoszą się do dokumentacji zestawu SDK dodatku do kontroli źródła.  
  
## <a name="definitions"></a>Definicje  
 Zaewidencjonowania  
 Gdy użytkownik wprowadza zmiany w roboczej kopii, użytkownik musi wysłać zmiany z kopii roboczej do centralnego repozytorium kontroli źródła. Spowoduje to utworzenie nowej wersji pliku, który jest dostępny dla innych użytkowników. Ten proces jest nazywany zaewidencjonowaniam.  
  
 Checkout  
 Czynność żądająca kopii roboczej z repozytorium, informująca o zamiarze zmodyfikowania repozytorium. Kopia robocza odzwierciedla stan projektu od momentu wyewidencjonowania.  
  
 Klient  
 Program korzystający z systemu kontroli kodu źródłowego. Na potrzeby tej dokumentacji jest to środowisko IDE programu Visual Studio.  
  
 Komentarz  
 Komunikat opisujący zmiany, które użytkownik może dołączyć do poprawki podczas wykonywania operacji kontroli źródła.  
  
 Konflikt  
 Sytuacja, w której dwaj użytkownicy próbują zaewidencjonować zmiany w tym samym regionie tego samego pliku. Zwykle należy wykonać scalanie.  
  
 Katalog  
 Folder lokalny po stronie klienta jest określany jako katalog. Jest to kopia, w której użytkownik wprowadza zmiany. Może istnieć wiele kopii roboczych danego projektu; Ogólnie każdy deweloper ma własną kopię.  
  
 Get  
 Operacja get przywraca aktualną kopię roboczą użytkownika przy użyciu kopii repozytorium. W przeciwieństwie do wyewidencjonowania, pobieranie jest wykonywane, gdy użytkownik po prostu potrzebuje najnowszej kopii, ale nie wprowadza żadnych zmian.  
  
 Historia  
 Jest to zazwyczaj podsumowanie wszystkich wyewidencjonowania, zaewidencjonowania, aktualizacji, tagów i wydań wykonanych w repozytorium kontroli źródła.  
  
 IDE  
 Ogólnie dotyczy zintegrowanego środowiska projektowego programu Visual Studio. Jednak może ona również odnosić się do innych środowisk klienckich, które uznają interfejs API wtyczki kontroli źródła.  
  
 Merge  
 Proces polegający na tym, że co najmniej dwa pliki kodu źródłowego są łączone w celu utworzenia nowego pliku, który zawiera wszystkie funkcje z poprzednich plików. Koncepcja ta jest istotna w kontroli wersji, w której co najmniej dwaj deweloperzy pracują nad plikami jednocześnie.  
  
 Projekt  
 Folder kontroli źródła jest często określany jako projekt. Nie ma żadnych relacji z projektami ani rozwiązaniami w programie Visual Studio.  
  
 Wtyczka  
 Biblioteka DLL, która zapewnia funkcje kontroli źródła przez implementację interfejsu API wtyczki kontroli źródła.  
  
 Repozytorium  
 Kopia główna, w której system kontroli źródła przechowuje pełną historię poprawek projektu. Każdy projekt ma dokładnie jedno repozytorium.  
  
 Przegląd  
 Zatwierdzona zmiana w historii pliku lub zestawu plików. Poprawka jest jedną migawką w stale zmienianym projekcie.  
  
## <a name="see-also"></a>Zobacz też  
 [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
