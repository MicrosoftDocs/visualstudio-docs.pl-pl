---
title: Edytowanie testów obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Editor
- load tests, Load Test Editor
ms.assetid: ba16ed02-137e-40bf-a4cb-45d87d922d37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 130f7296985aa5c5e6115cd3e61b00efd90f25c7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62784052"
---
# <a name="edit-load-tests"></a>Edytowanie testów obciążenia

Testy obciążenia przebiegu testu wydajności WWW lub testów jednostkowych, aby zasymulować wielu użytkownikom dostęp do serwera, w tym samym czasie. Test obciążeniowy umożliwia dostęp do danych obciążeniowych i wydajnościowych aplikacji. Test obciążeniowy można skonfigurować tak, aby emulował różne warunki obciążenia, np. obciążenie przez użytkowników i typy sieci.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Test obciążenia jest definiowany przez *scenariuszy*, *zbiory liczników*, i *parametrów uruchomieniowych*. Na poniższej ilustracji wyjaśnia różnice między [scenariuszy](../test/edit-load-test-scenarios.md), [zbiory liczników](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md), i [parametrów uruchomieniowych](../test/load-test-run-settings-properties.md):

![Architektura testu obciążenia](../test/media/load_test_editor.png)

## <a name="software-requirements"></a>Wymagania dotyczące oprogramowania

Projekty testów wydajności i obciążenia sieci Web są dostępne tylko w wersji Enterprise programu Visual Studio.

## <a name="edit-load-test-scenario-settings"></a>Edytowanie ustawień scenariusza testu obciążeniowego

Scenariusz służy do modelowania współdziałania grupy użytkowników z aplikacji serwera. Scenariusz składa się z wzorca obciążenia, modelu testu mieszanego, testu mieszanego, mieszanej przeglądarki i mieszanego profilu sieciowego. Test obciążenia może mieć więcej niż jeden scenariusz, a jeden scenariusz może zawierać testy wydajności sieci web i testów jednostkowych. Grupując podobne ustawienia, scenariusz umożliwia łączenie i wspólne wykonywanie testów o podobnym charakterze.

Aby uzyskać więcej informacji, zobacz [scenariusze testów obciążenia edycji](../test/edit-load-test-scenarios.md) i [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

## <a name="configure-and-manage-performance-counter-sets"></a>Konfigurowanie i zarządzanie zbiorami liczników wydajności

Testy obciążenia dostarczają nazwanych zestawów licznika, uporządkowanych według technologii, które są przydatne podczas analizowania danych licznika wydajności. Zestawy liczników obejmują Test obciążenia, IIS, ASP.NET i SQL. Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążeniowego**, początkowy zestaw wstępnie zdefiniowanych i ważnych liczników jest skonfigurowany dla komputerów, które określono jako uwzględniane w teście obciążeniowym. Zarządzasz licznikami w **edytora testu obciążenia**.

Aby uzyskać więcej informacji, zobacz [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążeniowym](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="configure-and-manage-load-test-run-settings"></a>Konfigurowanie i zarządzanie nimi uruchomieniowych testu obciążeniowego

Ustawienia uruchamiania są właściwości, które mają wpływ na sposób, w jaki przebieg testu obciążeniowego. Ustawienia uruchamiania są zorganizowane według kategorii w **właściwości** okna.

Aby uzyskać więcej informacji, zobacz [parametrów uruchomieniowych testu obciążeniowego Konfiguruj](../test/configure-load-test-run-settings.md) i [właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizowanie naruszeń zasady progu](../test/analyze-threshold-rule-violations-in-load-tests.md)