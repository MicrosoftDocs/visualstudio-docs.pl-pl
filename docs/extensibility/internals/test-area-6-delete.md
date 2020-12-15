---
title: 'Obszar testowy 6: usuwanie | Microsoft Docs'
description: Ten obszar testowania kontroli źródła obejmuje akcje usuwania w Eksplorator rozwiązań dla wtyczki kontroli źródła programu Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1371472a4dec265b5e476d96a32cb725e91ce7fe
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487559"
---
# <a name="test-area-6-delete"></a>Obszar testowy 6: Usuwanie
Ten obszar testowania wtyczki kontroli źródła obejmuje akcje usuwania.

 Kontrola źródła reaguje na usunięcie akcji w **Eksplorator rozwiązań**.

 Poniżej znajduje się lista elementów, które mogą zostać usunięte:

- Files

- Foldery

- Project

  W zależności od typu projektu może istnieć możliwość **usunięcia** projektu (pozostawia pliki na dysku) lub **usunięcia** projektu (usuwa pliki na dysku). Każda akcja powoduje usunięcie projektu lub elementu z **Eksplorator rozwiązań**.

## <a name="expected-behavior"></a>Oczekiwane zachowanie
 Oczekiwane zachowanie przypadków testowych w obszarze testowym usuwania to:

- Usunięty element nie jest już widoczny w **Eksplorator rozwiązań**.

- Element nadrzędny usuniętego projektu lub elementu jest wyewidencjonowany w razie potrzeby (prawdopodobnie z monitem).

- Po usunięciu wyewidencjonowanego lub dodanego elementu nie jest on wyświetlany w oknie **Oczekujące zaewidencjonowania** .

- Element nadal istnieje w magazynie kontroli źródła, nawet po usunięciu, i musi zostać ręcznie przeczyszczony.

|Akcja|Kroki testu|Oczekiwane wyniki do zweryfikowania|
|------------|----------------|--------------------------------|
|Usuwanie projektu klienta|1. Utwórz projekt klienta.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Usuń cały projekt z rozwiązania|Typowe oczekiwane zachowanie.|
|Usuń pusty plik|1. Utwórz projekt klienta.<br />2. Dodaj plik o zerowej bajcie do projektu.<br />3. Dodaj rozwiązanie do kontroli źródła.<br />4. Wybierz plik, a następnie usuń go.|Typowe oczekiwane zachowanie.|
|Usuń folder z jednym plikiem|1. Utwórz rozwiązanie pojedynczego projektu.<br />2. Dodaj folder.<br />3. Dodaj jeden plik do folderu.<br />4. Dodaj rozwiązanie do kontroli źródła.<br />5. Sprawdź projekt, aby uniknąć wyświetlania.<br />6. Usuń folder.|Typowe oczekiwane zachowanie.|
|Usuń projekt sieci Web systemu plików|1. Utwórz projekt sieci Web systemu plików (Użyj przycisku Przeglądaj, aby określić ścieżkę UNC).<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Usuń cały projekt z rozwiązania.<br />4. Powtórz kroki od 1 do 3 dla lokalnego projektu sieci Web (wykonuje różne ścieżki poprzez kod, ale ma ten sam interfejs zewnętrzny i zachowanie).|Typowe oczekiwane zachowanie.|
|Usuń plik z projektu sieci Web systemu plików|1. Utwórz projekt systemu plików w sieci Web.<br />2. Dodaj rozwiązanie do kontroli źródła.<br />3. Usuń plik z projektu.<br />4. Powtórz kroki od 1 do 3 dla lokalnego projektu sieci Web (wykonuje różne ścieżki poprzez kod, ale ma ten sam interfejs zewnętrzny i zachowanie).|Typowe oczekiwane zachowanie.|

## <a name="see-also"></a>Zobacz także
- [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
