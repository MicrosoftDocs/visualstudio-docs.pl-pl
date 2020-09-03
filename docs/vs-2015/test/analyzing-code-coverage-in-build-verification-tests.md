---
title: Analizowanie pokrycia kodu w testach weryfikacji kompilacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 59c07d15-511e-4fd0-b398-bde9d5ed00d9
caps.latest.revision: 10
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2442bf4cc31eeb51332aa28325924e18ccb1ffb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660727"
---
# <a name="analyzing-code-coverage-in-build-verification-tests"></a>Analiza pokrycia kodu w testach weryfikacji kompilacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Analiza pokrycia kodu w Microsoft Visual Studio pokazuje, ile kodu jest wykonywanych przez testy automatyczne. Aby uzyskać więcej informacji, zobacz [Korzystanie z pokrycia kodu w celu określenia, ile kodu jest testowany](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

 Podczas sprawdzania kodu testy będą uruchamiane na serwerze kompilacji, razem z innymi testami pozostałych członków zespołu. (Jeśli jeszcze tego nie zrobiono, zobacz [Uruchamianie testów w procesie kompilacji](https://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38)). Warto analizować pokrycie kodu w usłudze kompilacji, ponieważ zapewnia to najbardziej aktualne i kompleksowe zdjęcie pokrycia w całym projekcie. Zawiera także automatyczne testy systemu i inne zakodowane testy, których zwykle nie uruchamia się na komputerach deweloperskich.

1. W Team Explorer Otwórz **kompilacje**, a następnie Dodaj lub Edytuj definicję kompilacji.

2. Na stronie **proces** rozwiń węzeł **testy automatyczne**, **Źródło testów**, **Parametry uruchomieniowe**. Ustaw **Typ pliku parametrów uruchomieniowych** na **włączony pokrycie kodu**.

    Jeśli masz więcej niż jedną definicję źródła testów, powtórz ten krok dla każdej z nich.

   - <em>Ale nie istnieje pole o nazwie **typu pliku parametrów uruchomieniowych</em>*. *

      W obszarze **testy automatyczne**wybierz pozycję **zestaw testowy** i wybierz przycisk wielokropka **[...]** na końcu wiersza. W oknie dialogowym **Dodawanie/edytowanie przebiegu testu** w obszarze moduł uruchamiający **testy**wybierz pozycję **Visual Studio Test Runner**.

   ![Ustawianie definicji kompilacji dla pokrycia kodu](../test/media/codecoverage-plaincc.png "CodeCoverage — plainCC")

   Po uruchomieniu kompilacji wyniki pokrycia kodu pojawiają się w podsumowaniu kompilacji.

## <a name="see-also"></a>Zobacz też
 [Korzystanie z pokrycia kodu do określania, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
