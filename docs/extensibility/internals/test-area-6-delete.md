---
title: 'Obszar badania 6: Usuń | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9902ab9d1cb9c28ddf67b83590a4cccd5f6562f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704509"
---
# <a name="test-area-6-delete"></a>Obszar testowy 6: usuwanie
Ten obszar testu wtyczki kontroli źródła obejmuje akcje usuwania.

 Kontrola źródła reaguje na akcje usuwania w **Eksploratorze rozwiązań**.

 Poniżej znajduje się lista elementów, które można usunąć:

- Pliki

- Foldery

- Projekt

  W zależności od typu projektu może być dostępna opcja **Usuń** projekt (pozostawia pliki na dysku) lub **Usuń** projekt (usuwa pliki na dysku). Akcja usuwa projekt lub element z **Eksploratora rozwiązań**.

## <a name="expected-behavior"></a>Oczekiwane zachowanie
 Oczekiwane zachowanie dla przypadków testowych w obszarze testu usuwania jest:

- Usunięty element nie jest już widoczny w **Eksploratorze rozwiązań**.

- Element nadrzędny usuniętego projektu lub elementu jest wyewidencjonowany zgodnie z potrzebami (prawdopodobnie z monitem).

- Po usunięciu wyewidencjonowanego lub dodanego elementu NIE pojawi się on w oknie **Oczekujące zaewidencjonowania.**

- Element nadal istnieje w magazynie kontroli źródła, nawet po usunięciu i musi być ręcznie czyszty.

|Akcja|Etapy testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Usuwanie projektu klienta|1. Utwórz projekt klienta.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Usuń cały projekt z rozwiązania|Typowe oczekiwane zachowanie.|
|Usuwanie pustego pliku|1. Utwórz projekt klienta.<br />2. Dodaj plik bajtów zero do projektu.<br />3. Dodaj rozwiązanie do kontroli źródła.<br />4. Wybierz plik, usuń go.|Typowe oczekiwane zachowanie.|
|Usuwanie folderu z jednym plikiem|1. Tworzenie rozwiązania pojedynczego projektu.<br />2. Dodaj folder.<br />3. Dodaj jeden plik do folderu.<br />4. Dodaj rozwiązanie do kontroli źródła.<br />5. Sprawdź projekt, aby uniknąć monitów.<br />6. Usuń folder.|Typowe oczekiwane zachowanie.|
|Usuwanie projektu sieci Web systemu plików|1. Utwórz projekt sieci Web systemu plików (użyj przycisku Przeglądaj, aby określić ścieżkę UNC).<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Usuń cały projekt z rozwiązania.<br />4. Powtórz kroki od 1 do 3 dla lokalnego projektu sieci Web (wykonuje różne ścieżki za pośrednictwem kodu, ale ma ten sam interfejs zewnętrzny i zachowanie).|Typowe oczekiwane zachowanie.|
|Usuwanie pliku z projektu sieci Web systemu plików|1. Utwórz projekt sieci Web systemu plików.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Usuń plik z projektu.<br />4. Powtórz kroki od 1 do 3 dla lokalnego projektu sieci Web (wykonuje różne ścieżki za pośrednictwem kodu, ale ma ten sam interfejs zewnętrzny i zachowanie).|Typowe oczekiwane zachowanie.|

## <a name="see-also"></a>Zobacz też
- [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
