---
title: Legenda widoku rdzeni | Microsoft Docs
description: Dowiedz się więcej o legendzie widoku rdzeni, która udostępnia dane przełącznika kontekstu tabelarycznego i wybór wątku. Poznaj również informacje o przełącznikach kontekstu i wydajności.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cores.legend
helpviewer_keywords:
- Concurrency Visualizer, Cores View Legend
ms.assetid: e160384c-fcfe-49b3-86b7-229adb736c51
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e4486bc20caf580c9a2c1038002693bd92fe616a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882924"
---
# <a name="cores-view-legend"></a>Legenda widoku rdzeni
Legenda widoku rdzeni identyfikuje każdy wątek według koloru i nazwy. Zawiera kolumny, które pokazują liczbę przełączeń kontekstu między rdzeniami, łączne przełączenia kontekstu i procent przełączeń kontekstu między rdzeniami. Wiersze w legendzie są sortowane według liczby przełączeń kontekstu między rdzeniami, w kolejności malejącej.

 Możesz wybrać wiersze w legendzie, aby odfiltrować wątki, które są wyświetlane na osi czasu. Na osi czasu są wyświetlane tylko wybrane wątki. Jeśli nie wybrano żadnych wierszy, wszystkie wiersze są wyświetlane na osi czasu.

 W przypadku wielu rdzeni przełączanie jest droższe niż w przypadku przełączników, które pozostają w tym samym rdzeniu logicznym. W trakcie przełączania kontekstu rejestry procesora są zapisywane i przywracane, kod jądra systemu operacyjnego jest wykonywany, zostaną ponownie załadowane wpisy bufora referencyjna translacji i potok procesora jest opróżniany. Przełączenia kontekstu między rdzeniami mogą być jeszcze droższe niż inne przełączenia kontekstu, ponieważ dane pamięci podręcznej są nieprawidłowe dla tego wątku na innym rdzeńu. W przeciwieństwie do tego, czy wątek został przełączony do kontekstu na rdzeń, który wcześniej działał, prawdopodobnie przydatne dane nadal są w pamięci podręcznej. W przypadku zwiększenia liczby przełączeń kontekstu między rdzeniami przez podejmowanie prób zarządzania koligacją wątku i wydajności należy rozważyć, czy należy rozwiązać ten problem. Zacznij od wyeliminowania koligacji wątku, a następnie Obserwuj wyniki działania między rdzeniami.

 W poniższej tabeli opisano elementy legendy.

|Element|Definicja|
|-------------|----------------|
|Nazwa wątku|Pokazuje kolor wątku w poprzedniej osi czasu rdzeni i nazwę tego wątku.|
|Przełączenia kontekstu między rdzeniami|Liczba przełączeń kontekstu dla wątku, które również przełączają się z jednego rdzenia logicznego na inny. Nie różni się między wielordzeniowymi przełącznikami kontekstowymi, które przechodzą z jednego procesora do drugiego, a te, które pozostają w tej samej operacji.|
|Łączna Liczba przełączeń kontekstu|Całkowita liczba przełączeń kontekstu dla danego wątku w okresie próbkowania. Za każdym razem, gdy wątek zmienia kontekst (na przykład z wykonywania do synchronizacji), jest zliczane jeden przełącznik kontekstu.|
|Procent przełączeń kontekstu, które przekraczają rdzenie|Obliczany jako wartość procentowa przez podzielenie liczby przełączeń kontekstu między rdzeniami przez liczbę przełączników całkowitego kontekstu. Im wyższa wartość procentowa, tym większy wpływ narzutu na przełączenia kontekstu między rdzeniami na wydajność tego określonego wątku.|

## <a name="see-also"></a>Zobacz też
- [Widok rdzeni](../profiling/cores-view.md)