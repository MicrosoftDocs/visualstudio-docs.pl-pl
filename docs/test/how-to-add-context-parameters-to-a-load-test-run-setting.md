---
title: Dodawanie parametrów kontekstu do ustawienia przebiegu testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, context parameters
- load tests, context parameters
ms.assetid: a8a0b97e-8040-4711-85ab-36548b130ed2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 05efbba005a9455af3b9d2e8755b580a8af30d0a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584481"
---
# <a name="how-to-add-context-parameters-to-a-load-test-run-setting"></a>Jak: Dodawanie parametrów kontekstu do ustawienia przebiegu testu obciążenia

Po utworzeniu testu obciążenia przy użyciu **Kreatora nowego testu obciążenia**można użyć **Edytora testów obciążenia,** aby zmienić właściwości scenariuszy, aby spełnić twoje potrzeby i cele testowania.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Aby uzyskać pełną listę właściwości ustawień uruchamiania i ich opisy, zobacz [Właściwości ustawień przebiegu testu ładowania](../test/load-test-run-settings-properties.md).

Można utworzyć parametry kontekstu do użycia w ustawieniu przebiegu testu obciążenia przy użyciu Edytora testów obciążenia. Parametry kontekstu umożliwiają parametryzację ciągu.

Załóżmy, że test obciążenia zawiera test wydajności sieci web, który już używa sparametryzowanego adresu URL serwera sieci web przy użyciu parametru kontekstu. Można dodać parametr kontekstu do ustawienia przebiegu testu obciążenia, który używa tej samej wartości nazwy, co ta, która jest używana w teście wydajności sieci web. Spowoduje to mapowanie testu wydajności sieci web na inny serwer po uruchomieniu testu obciążenia. Na przykład jeśli test obciążenia zawiera test wydajności sieci web, który używa parametru kontekstu o nazwie WebServer1 dla nazwy serwera sieci web w adresie URL. Jeśli następnie określisz parametr kontekstu w ustawieniu przebiegu testu obciążenia, który jest również nazwany WebServer1, test obciążenia użyje parametru kontekstu, który został przypisany w ustawieniu przebiegu testu obciążenia. Aby wyjaśnić, jeśli test wydajności sieci web w teście obciążenia używa tej samej nazwy parametru kontekstu jako parametru kontekstu w teście obciążenia, parametr kontekstu w teście obciążenia zastąpi parametr kontekstu, który jest używany w teście wydajności sieci web.

> [!WARNING]
> Należy uważać, aby nie przypadkowo zastąpić parametr kontekstu testu wydajności sieci web, gdy używasz parametrów kontekstu w ustawieniu uruchamiania. Należy unikać używania tych samych nazw parametrów kontekstu, chyba że to zrobić celowo.

Jeśli do programu zostanie przypisana wartość parametru kontekstu `http://CorporateStagingWebServer` `WebServer1` Webserver1, można użyć w całym teście obciążenia, a tym samym łatwo zmienić wartość na inny serwer sieci web w dowolnym momencie.

Ponadto przypisując różne wartości do parametru kontekstu przy użyciu tej samej nazwy w różnych ustawieniach przebiegu testu obciążenia, można uruchomić test obciążenia przy użyciu różnych środowisk:

- Ustawienie uruchamiania korporacyjnego serwera przemieszczania sieci Web: parametr kontekstu o nazwie`WebServer1=http://CorporateStagingWebServer`

- Uruchamianie uruchamiania firmowego serwera sieci Web: parametr Kontekst o nazwie`WebServer1=http://CorporateProductionWebServer`

  **Zmiana ustawienia uruchamiania z wiersza polecenia**

  Jeśli chcesz użyć różnych ustawień uruchamiania z wiersza polecenia, aby skorzystać ze strategii parametrów kontekstu, użyj następujących poleceń:

  **Set Test.UseRunSetting= Serwer FirmSagingWeb**

  -i-

  **mstest /testcontainer:loadtest1.loadtest**

## <a name="to-add-a-context-parameter-to-a-run-setting"></a>Aby dodać parametr kontekstu do ustawienia uruchamiania

1. Otwórz test obciążenia.

2. Rozwiń folder **Uruchom ustawienia** w drzewie testu obciążenia w Edytorze testów obciążenia.

3. Kliknij prawym przyciskiem myszy określone ustawienie uruchamiania, do którego chcesz dodać parametr kontekstu, a następnie wybierz polecenie **Dodaj parametr kontekstu**.

     Nowy parametr kontekstu jest dodawany do folderu **Parametry kontekstu** w folderze **Uruchom ustawienia** w drzewie testu obciążenia.

     — lub —

     Jeśli ustawienie uruchamiania zawiera już folder **Parametry kontekstu,** można go kliknąć prawym przyciskiem myszy, a następnie wybrać polecenie **Dodaj parametr kontekstu**.

4. W oknie **Właściwości** zmień odpowiednią wartość **name** (na przykład WebServer1). W oknie **Właściwości** zmień **wartość** na parametr, którego chcesz użyć `http://CorporateStagingWebServer`(na przykład ).

5. (Opcjonalnie) Powtórz kroki od 3 do 5 i użyj innego `http://CorporateProductionWebServer`ciągu dla właściwości **Value** (na przykład ).

6. Wybierz ustawienia uruchamiania, które mają być aktywne. Otwórz menu skrótów w ustawieniach uruchamiania i wybierz pozycję **Ustaw jako aktywny**.

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie ustawień przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
