---
title: Dodawanie parametrów kontekstu do ustawień uruchomienia testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, context parameters
- load tests, context parameters
ms.assetid: a8a0b97e-8040-4711-85ab-36548b130ed2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b979da03c0ea5378684ff12bc86d4fb59eef9180
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979459"
---
# <a name="how-to-add-context-parameters-to-a-load-test-run-setting"></a>Instrukcje: Dodawanie parametrów kontekstu do ustawień przebiegu testu obciążeniowego

Po utworzeniu testu obciążenia przy użyciu **Kreatora nowego testu obciążeniowego**, możesz użyć **edytora testu obciążenia** można zmienić właściwości scenariuszy do spełnienia potrzeb i celów testowania.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Aby uzyskać pełną listę właściwości parametrów uruchomieniowych i ich opisów, zobacz [właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).

Można utworzyć parametrów kontekstu do użycia w teście obciążeniowym, ustawienia uruchamiania za pomocą edytora testu obciążenia. Parametry kontekstu umożliwiają definiowanie parametrów ciągu.

Załóżmy, że test obciążenia zawiera test wydajności sieci web, który używa już sparametryzowane internetowy adres URL serwera za pomocą parametru kontekstu. Możesz dodać parametr kontekstu do testu obciążenia uruchomieniowy, który używa tej samej wartości Nazwa, która jest używana podczas testów wydajności sieci web. Będzie to mapować testu wydajności sieci web na innym serwerze, po uruchomieniu testu obciążenia. Na przykład jeśli test obciążenia zawiera test wydajności sieci web, który używa parametru kontekstu o nazwie Serwer_sieci_web_1 dla nazwy serwera sieci web w adresie URL. Jeśli następnie możesz określić parametr kontekstowy w teście obciążenia uruchomieniowy, który jest również określany Serwer_sieci_web_1, test obciążeniowy użyje parametru kontekstowego, który można przypisać w uruchomieniowych testu obciążeniowego. Wyjaśnienie, jeśli test wydajności sieci web w teście obciążeniowym używa tego samego Nazwa parametru kontekstu jako parametru kontekstu w teście obciążeniowym, parametru kontekstowego w teście obciążenia spowoduje zastąpienie parametru kontekstowego, który jest używany podczas testu wydajności sieci web.

> [!WARNING]
> Uważaj, aby nie przypadkowo zastąpienia parametru kontekstu testu wydajności sieci web, korzystając z parametrów kontekstu w ustawieniach testu. Należy unikać używania tych samych nazw parametrów kontekstu, chyba że w tym celowo.

Jeśli przypisujesz wartość parametru kontekstowego serwer_sieci_Web_1 do `http://CorporateStagingWebServer`, można użyć `WebServer1` w całym obciążenia testu i dzięki temu łatwo zmienić wartości do różnych serwerów sieci web w dowolnym momencie.

Ponadto, przypisując różne wartości do parametru kontekstu przy użyciu tej samej nazwie w uruchomieniowych testu obciążeniowego różnych, można uruchomić testu obciążeniowego za pomocą różnych środowiskach:

- Serwer sieci Web firmy przemieszczania uruchomieniowy: Parametr kontekstowy o nazwie `WebServer1=http://CorporateStagingWebServer`

- Ustawienia uruchamiania firmowy serwer sieci Web w środowisku produkcyjnym: Parametr kontekstowy o nazwie `WebServer1=http://CorporateProductionWebServer`

  **Zmienianie ustawień wykonywania w wierszu polecenia**

  Jeśli chcesz korzystać z zalet strategii parametru kontekstu przy użyciu różnych parametrów uruchomieniowych z wiersza polecenia, użyj następujących poleceń:

  **Set Test.UseRunSetting= CorporateStagingWebServer**

  - i -

  **mstest /testcontainer:loadtest1.loadtest**

## <a name="to-add-a-context-parameter-to-a-run-setting"></a>Aby dodać parametr kontekstu do ustawień

1. Otwórz test obciążenia.

2. Rozwiń **parametrów uruchomieniowych** folderów w drzewie testu obciążenia w edytorze testu obciążeniowego.

3. Kliknij prawym przyciskiem myszy konkretne ustawienia uruchamiania, do której chcesz dodać parametr kontekstu, a następnie wybierz **dodać parametr kontekstu**.

     Dodano nowy parametr kontekstu do **parametrów kontekstu** folderu w **parametrów uruchomieniowych** folderu w drzewie testu obciążenia.

     —lub—

     Jeśli działanie ustawienie już zawiera **parametrów kontekstu** folderu, możesz go prawym przyciskiem myszy i wybierz **dodać parametr kontekstu**.

4. W **właściwości** okna, zmień wartość **nazwa** odpowiednio (na przykład Serwer_sieci_web_1). W **właściwości** oknie zmiany **wartość** do parametru, którego chcesz używać (na przykład `http://CorporateStagingWebServer`).

5. (Opcjonalnie) Powtórz kroki od 3 do 5 i używać różnych ciąg **wartość** właściwości (na przykład `http://CorporateProductionWebServer`).

6. Wybierz opcję uruchamiania ustawień, które mają być aktywne. Otwórz menu skrótów dotyczące wykonywania ustawień, a następnie wybierz **Ustaw jako aktywny**.

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)