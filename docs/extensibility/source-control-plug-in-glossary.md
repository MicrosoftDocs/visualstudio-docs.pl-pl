---
title: Słownik wtyczki kontroli źródła | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 47488621fe3e5167e00442e1ca971ef923d9b25c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331910"
---
# <a name="source-control-plug-in-glossary"></a>Słownik wtyczki kontroli źródła
Następujące przydatne terminów i definicje odnoszą się do dokumentacji zestawu SDK wtyczki kontroli źródła.

## <a name="definitions"></a>Definicje
 Ewidencjonowanie, gdy użytkownik wprowadzi zmiany do kopii roboczej, użytkownik musi wysłać zmiany z kopii roboczej w repozytorium kontroli źródła centralnej. Spowoduje to utworzenie nowej wersji pliku, który jest dostępny dla innych użytkowników. Ten proces jest nazywany zaewidencjonowania.

 Wyewidencjonuj czynność żądania jako kopia robocza zawartości z repozytorium, z informacją o tym repozytorium zgodne z zamiarami użytkownika go zmodyfikować. Kopia robocza odzwierciedla stan projektu, począwszy od tej chwili, który został wyewidencjonowany.

 Program kliencki element, który korzysta z systemu kontroli kodu źródłowego. Na potrzeby niniejszej dokumentacji jest środowiska IDE programu Visual Studio.

 Komunikat komentarz A, opisująca zmiany, które użytkownika mogą dołączać do poprawki, gdy jest wykonywana operacja kontroli źródła.

 Konflikt A sytuacji, gdy dwóch użytkowników próbuje zaewidencjonować zmieni się na tym samym regionie, w tym samym pliku. Zwykle muszą być wykonywane scalanie.

 Folder lokalny katalog A po stronie klienta jest określone jako katalog. Jest to kopia, w której użytkownik faktycznie sprawia, że zmiany. Może istnieć wiele kopii roboczych danego projektu; Zazwyczaj każdy Deweloper ma swoją kopię.

 Operacji get A pobierania łączy użytkownika kopia robocza bądź na bieżąco z kopią repozytorium. W przeciwieństwie do wyewidencjonowania get jest wykonywane, gdy użytkownik po prostu wymaga najnowszej kopii, ale zamierza nie wprowadzaj żadnych zmian.

 Historia, który zazwyczaj znajduje się podsumowanie wszystkich wyewidencjonowania, elementy do zaewidencjonowania, aktualizacje, tagi i wydań w repozytorium kontroli źródła.

 Środowisko IDE na ogół odnosi się do programu Visual Studio zintegrowane środowisko projektowe. Jednakże można także zapoznać się inne środowiska klienta, które rozpoznają API wtyczki kontroli źródła.

 Scal procesu, podczas których źródła dwóch lub więcej plików kodu są łączone w celu utworzenia nowego pliku, który zawiera wszystkie funkcje z poprzednich plików. Takie podejście jest w kontroli wersji którym co najmniej dwóch deweloperzy pracują na plikach jednocześnie.

 Folder kontroli źródła projektu, A często nazywa się projekt. To nie ma żadnych relacji z projektów i rozwiązań w programie Visual Studio.

 DLL dodatku typu plug-in, który zapewnia funkcji kontroli źródła, implementując interfejs API wtyczki kontroli źródła.

 Repozytorium kopii głównej, której system kontroli źródła przechowuje historię pełną wersję projektu. Każdy projekt ma dokładnie jedno repozytorium.

 Korekta A zatwierdzone zmiany w historii pliku lub zestawu plików. Zmiana jest jeden migawki w projekcie stale zmieniających.

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)