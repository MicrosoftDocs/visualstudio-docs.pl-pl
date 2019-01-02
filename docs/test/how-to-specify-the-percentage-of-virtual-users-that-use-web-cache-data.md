---
title: Określ wartości procentowej użytkowników wirtualnych danych pamięci podręcznej sieci Web użycie dla testów obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual users
ms.assetid: f66d5d43-4121-4487-b27f-d0a0baaf7601
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: c9cf6ea3b5bf82d26ab838b75cb0c0092aafc182
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958764"
---
# <a name="how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data"></a>Instrukcje: Określ wartość procentową użytkowników wirtualnych korzystających z danych w pamięci podręcznej sieci web

Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążeniowego**, można zmienić właściwości scenariuszy do spełnienia potrzeb i celów testowania przy użyciu **edytora testu obciążenia**. Aby uzyskać pełną listę właściwości scenariusza testów obciążenia wraz z opisami, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Procent nowych użytkowników** właściwość jest ustawiona **właściwości** okna. Edytuj właściwości scenariusza testów obciążenia w **edytora testu obciążenia**.

**Procent nowych użytkowników** właściwość ma wpływ na sposób, w którym zasymulowano obciążenie krokowe buforowania zostałyby wykonane przez przeglądarkę sieci web. Domyślnie **procent nowych użytkowników** właściwość jest ustawiona na 0%. Jeśli wartość **procent nowych użytkowników** właściwość jest ustawiona na 100%, każdy test wydajności sieci web, uruchom w teście obciążeniowym jest traktowany jak witrynę po raz pierwszy do witryny internetowej który nie ma żadnej zawartości z witryny sieci Web w swojej pamięci podręcznej przeglądarki, z poprzednie wizyty. W efekcie wszystkie żądania w teście sieci web, w tym wszystkich żądań zależnych, taką jak obrazy, zostaną pobrane.

> [!NOTE]
> Jeśli ten sam zasób podlega buforowaniu, wymagane są więcej niż raz w teście sieci web, żądania nie zostaną pobrane.

Jeśli jesteś obciążeniowy witryny sieci Web, która zawiera szereg istotnych zwracany użytkowników, którzy mogą mieć obrazów i innych podlega buforowaniu zawartości lokalnie w pamięci podręcznej, następnie ustawienie 100% **procent nowych użytkowników** właściwość wygeneruje więcej żądania pobierania nie może mieć miejsce w wykorzystanie w świecie rzeczywistym. W takim przypadku należy oszacować procentową wizyt do witryny sieci Web, które pochodzą z pierwszym uruchomieniu witryny sieci Web, a następnie ustaw **procent nowych użytkowników** właściwość odpowiednio.

## <a name="to-specify-the-percentage-of-new-users-for-a-scenario"></a>Aby określić procent nowych użytkowników na potrzeby scenariusza

1. Otwórz test obciążenia.

     **Edytora testu obciążenia** pojawia się. Zostanie wyświetlone drzewo testu obciążenia.

2. Obciążenia test drzew **scenariuszy** folderu, wybierz węzeł scenariusz, aby zmienić nową wartość procentową użytkownika dla.

3. Na **widoku** menu, wybierz opcję **okno właściwości**.

     Kategorie i właściwości tego scenariusza są wyświetlane w **właściwości** okna.

4. Ustaw wartość **procent nowych użytkowników** właściwość, według numerem procent nowych użytkowników.

5. Po zakończeniu, zmiana wartości właściwości, wybierz **Zapisz** na **pliku** menu. Następnie możesz uruchomić test obciążenia za pomocą nowego **procent nowych użytkowników** wartość.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Przewodnik: Tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)
- [Edytowanie wzorców obciążenia w celu modelu aktywności wirtualnych użytkowników](../test/edit-load-patterns-to-model-virtual-user-activities.md)