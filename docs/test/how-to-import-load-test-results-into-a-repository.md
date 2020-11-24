---
title: 'Porady: importowanie wyników testu obciążenia do repozytorium'
description: Dowiedz się, jak ładować informacje do repozytorium Wyniki testów obciążenia, korzystając z okna dialogowego Otwórz i Zarządzaj Wyniki testów ładowania.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- results, load test
- load test results, importing
- Load Test Results Repository
- load tests, importing results
ms.assetid: a955b3d2-c8ad-40dd-8ea3-9f1a271e1eed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2133977de827fe558ee9323280c5f05df683ed59
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442316"
---
# <a name="how-to-import-load-test-results-into-a-repository"></a>Instrukcje: Importowanie wyników testu obciążenia do repozytorium

Podczas wykonywania testu obciążeniowego informacje zebrane w trakcie sesji są zapisywane w repozytorium wyników testu obciążeniowego. Repozytorium to zawiera dane licznika wydajności oraz informacje o wszelkich błędach. Aby uzyskać więcej informacji, zobacz [Zarządzanie wynikami testów obciążenia w repozytorium wyniki testów ładowania](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Można zarządzać wynikami testów obciążenia z Edytor testu obciążeniowego przy użyciu okna dialogowego **Otwórz i zarządzaj wyniki testów ładowania** . Można otwierać, importować, eksportować i usuwać wyniki testów obciążenia.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-import-results-into-a-repository"></a>Aby zaimportować wyniki do repozytorium

1. Z projektu testu wydajności i obciążenia sieci Web Otwórz test obciążenia.

2. Na osadzonym pasku narzędzi wybierz pozycję **Otwórz i Zarządzaj wynikami**.

     Zostanie wyświetlone okno dialogowe **Otwórz i zarządzaj wyniki testów ładowania** .

3. W polu **Wprowadź nazwę kontrolera, aby znaleźć wyniki testu obciążenia**, wybierz kontroler. Wybierz **\<local>** , aby uzyskać dostęp do wyników przechowywanych lokalnie.

     Jeśli są dostępne wyniki testów obciążenia, są one wyświetlane na liście **wyników testu obciążenia** . Kolumny są typu **Time**, **Duration**, **User**, **wynik**, **test** i **Description**. **Test** zawiera nazwę testu, a **Opis** zawiera opcjonalny opis, który jest dodawany przed uruchomieniem testu.

4. Wybierz pozycję **Importuj**.

     Zostanie wyświetlone okno dialogowe **importuj wyniki testów ładowania** .

5. W polu **Nazwa pliku** wpisz nazwę zarchiwizowanego pliku wyników testu, a następnie wybierz **Otwórz**.

     \- oraz

     Przejdź do pliku, a następnie wybierz **Otwórz**.

    > [!NOTE]
    > Plik zarchiwizowanych wyników testu określony w tym kroku musi zostać utworzony przez wykonanie operacji eksportowania.

     Wyniki są importowane i pojawiają się na liście **wyników testu obciążenia** .

## <a name="see-also"></a>Zobacz także

- [Zarządzanie wynikami testów obciążenia w repozytorium Wyniki testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Instrukcje: Eksportowanie wyników testu obciążenia z repozytorium](../test/how-to-export-load-test-results-from-a-repository.md)
