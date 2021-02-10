---
title: Ustaw ustawienia przebiegu testu obciążenia z wiersza polecenia
description: Test obciążenia może obejmować Parametry uruchomieniowe, które mają wpływ na sposób uruchamiania testu obciążenia. Dowiedz się, jak ładować Parametry uruchomieniowe z wiersza polecenia.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, command line
- load tests, run settings, selecting
ms.assetid: 175d1d58-f09a-4449-b132-a29a394a7c8e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 872799a01e13ca94108f9acac655ee6541779c44
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971846"
---
# <a name="how-to-select-a-load-test-run-setting-to-use-from-the-command-line"></a>Instrukcje: Wybieranie ustawienia przebiegu testu obciążenia do użycia z wiersza polecenia

Test obciążenia może obejmować *Parametry uruchomieniowe*, które mają wpływ na sposób uruchamiania testu obciążenia. Parametry uruchomieniowe są zorganizowane według kategorii w oknie **Właściwości** . Po uruchomieniu testu obciążenia używa ustawienia uruchomieniowego, które jest obecnie ustawione jako aktywne.

Jeśli test obciążenia zawiera tylko jedno ustawienie uruchomieniowe, zawsze jest aktywnym węzłem. Jeśli test obciążenia zawiera wiele węzłów parametrów uruchomieniowych, można wybrać jeden do użycia podczas uruchamiania testu obciążenia z wiersza polecenia. Zobacz [jak: dodać dodatkowe parametry uruchomieniowe do testu obciążenia](../test/how-to-add-additional-run-settings-to-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-change-the-run-setting-from-the-command-line"></a>Aby zmienić ustawienie uruchomieniowe z wiersza polecenia

1. Jeśli chcesz użyć różnych parametrów uruchomieniowych z wiersza polecenia, aby skorzystać z strategii parametru kontekstowego, użyj następującego polecenia:

    `Set Test.UseRunSetting= CorporateStagingWebServer`

2. Uruchom test obciążenia przy użyciu MSTest:

    `mstest /testcontainer:loadtest1.loadtest`

## <a name="see-also"></a>Zobacz też

- [Skonfiguruj ustawienia przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
- [Określ zestawy liczników i reguły progowe dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Instrukcje: Dodawanie dodatkowych parametrów uruchomieniowych do testu obciążenia](../test/how-to-add-additional-run-settings-to-a-load-test.md)
- [Instrukcje: Wybieranie aktywnego ustawienia uruchomieniowego dla testu obciążenia](../test/how-to-select-the-active-run-setting-for-a-load-test.md)
