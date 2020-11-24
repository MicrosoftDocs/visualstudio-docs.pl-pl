---
title: Dodaj parametry kontekstu do ustawienia przebiegu testu obciążenia
description: Dowiedz się, jak utworzyć parametry kontekstu do użycia w ustawieniu przebiegu testu obciążenia przy użyciu Edytor testu obciążeniowego, które umożliwi Sparametryzuj ciągu.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings, context parameters
- load tests, context parameters
ms.assetid: a8a0b97e-8040-4711-85ab-36548b130ed2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 22b3a6a1f40a317284380bf72aadec4d53b6ce13
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440190"
---
# <a name="how-to-add-context-parameters-to-a-load-test-run-setting"></a>Instrukcje: Dodawanie parametrów kontekstu do ustawienia przebiegu testu obciążenia

Po utworzeniu testu obciążenia przy użyciu **nowego Kreator testu obciążeniowego** można użyć **Edytor testu obciążeniowego** , aby zmienić właściwości scenariuszy, aby spełniały potrzeby testowania i cele.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Aby zapoznać się z pełną listą właściwości parametrów uruchomieniowych i ich opisów, zobacz [właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).

Można utworzyć parametry kontekstu do użycia w ustawieniu przebiegu testu obciążenia przy użyciu Edytor testu obciążeniowego. Parametry kontekstu umożliwiają Sparametryzuj ciągu.

Załóżmy, że test obciążenia zawiera test wydajności sieci Web, który używa już sparametryzowanego adresu URL serwera sieci Web przy użyciu parametru kontekstowego. Można dodać parametr kontekstowy do ustawienia przebiegu testu obciążenia, który używa tej samej wartości nazwy co ta, która jest używana w teście wydajności sieci Web. Spowoduje to zamapowanie testu wydajności sieci Web na inny serwer podczas uruchamiania testu obciążenia. Na przykład jeśli test obciążenia zawiera test wydajności sieci Web, który używa parametru kontekstu o nazwie webserwer1 dla nazwy serwera sieci Web w adresie URL. Jeśli następnie określisz parametr kontekstowy w ustawieniu przebiegu testu obciążenia o nazwie webserwer1, test obciążenia użyje parametru kontekstowego, który został przypisany w ustawieniu przebiegu testu obciążenia. Aby wyjaśnić, jeśli test wydajności sieci Web w teście obciążenia używa tej samej nazwy parametru kontekstu jak parametr kontekstowy w teście obciążenia, parametr kontekstowy w teście obciążenia przesłoni parametr kontekstowy, który jest używany w teście wydajności sieci Web.

> [!WARNING]
> Należy zachować ostrożność, aby nie przesłonić parametru kontekstowego testu wydajności sieci Web w przypadku używania parametrów kontekstu w ustawieniach uruchamiania. Należy unikać używania tych samych nazw parametrów kontekstu, chyba że jest to celowe.

Jeśli przypiszesz wartość parametru kontekstowego webserwer1 do `http://CorporateStagingWebServer` , możesz użyć `WebServer1` całego testu obciążenia, a tym samym łatwo zmienić wartość na inny serwer sieci Web w dowolnym momencie.

Ponadto, przypisując różne wartości do parametru kontekstowego za pomocą tej samej nazwy w różnych ustawieniach przebiegu testu obciążenia, można uruchomić test obciążenia przy użyciu różnych środowisk:

- Ustawienie uruchomieniowe serwera sieci Web w firmie: parametr kontekstowy o nazwie `WebServer1=http://CorporateStagingWebServer`

- Ustawienie uruchomieniowe serwera sieci Web firmowego: parametr kontekstu o nazwie `WebServer1=http://CorporateProductionWebServer`

  **Zmiana ustawienia uruchomieniowego z wiersza polecenia**

  Jeśli chcesz użyć różnych parametrów uruchomieniowych z wiersza polecenia, aby skorzystać z strategii parametru kontekstowego, użyj następujących poleceń:

  **Ustaw test. UseRunSetting = CorporateStagingWebServer**

  lub

  **MSTest/testcontainer: LoadTest1. LoadTest**

## <a name="to-add-a-context-parameter-to-a-run-setting"></a>Aby dodać parametr kontekstowy do ustawienia przebiegu

1. Otwórz test obciążenia.

2. Rozwiń folder **Parametry uruchomieniowe** w drzewie testu obciążenia w Edytor testu obciążeniowego.

3. Kliknij prawym przyciskiem myszy konkretne ustawienie uruchomieniowe, do którego chcesz dodać parametr kontekstowy, a następnie wybierz polecenie **Dodaj parametr kontekstowy**.

     Nowy parametr kontekstowy jest dodawany do folderu **Parametry kontekstu** w folderze **Run Settings** w drzewie testu obciążenia.

     -lub-

     Jeśli ustawienie run zawiera już folder **parametrów kontekstu** , kliknij go prawym przyciskiem myszy, a następnie wybierz polecenie **Dodaj parametr kontekstowy**.

4. W oknie **Właściwości** Zmień wartość w polu **Nazwa** na odpowiednie (na przykład webserwer1). W oknie **Właściwości** Zmień **wartość** na parametr, który ma być używany (na przykład `http://CorporateStagingWebServer` ).

5. Obowiązkowe Powtórz kroki od 3 do 5 i użyj innego ciągu dla właściwości **Value** (na przykład `http://CorporateProductionWebServer` ).

6. Wybierz Parametry uruchomieniowe, które mają być aktywne. Otwórz menu skrótów na stronie Parametry uruchomieniowe i wybierz polecenie **Ustaw jako aktywne**.

## <a name="see-also"></a>Zobacz także

- [Skonfiguruj ustawienia przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
