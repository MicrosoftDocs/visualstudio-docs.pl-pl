---
title: Wybierz ustawienie uruchomieniowe dla testu obciążenia
description: Test obciążenia może obejmować Parametry uruchomieniowe, które mają wpływ na sposób uruchamiania testu obciążenia. Dowiedz się, jak wybrać aktywne ustawienie uruchomieniowe.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings, active
ms.assetid: ed6ff546-acfa-4dd8-b3a2-6e7455930ca4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: c93c636d8321affead3c3fce6f3074801cb9ae87
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882651"
---
# <a name="how-to-select-the-active-run-setting-for-a-load-test"></a>Instrukcje: Wybieranie aktywnego ustawienia uruchomieniowego dla testu obciążenia

Po utworzeniu testu obciążenia przy użyciu **nowego Kreator testu obciążeniowego** można użyć **Edytor testu obciążeniowego** , aby zmienić właściwości scenariuszy, aby spełniały potrzeby testowania i cele.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Test obciążenia może zawierać jedno lub więcej *parametrów uruchomieniowych* , które są zestawem właściwości, które wpływają na sposób przebiegu testu obciążenia. Parametry uruchomieniowe są zorganizowane według kategorii w oknie **Właściwości** . Po uruchomieniu testu obciążenia używa ustawienia uruchomieniowego, które jest obecnie ustawione jako aktywne.

> [!NOTE]
> Aby uzyskać pełną listę właściwości parametrów uruchomieniowych i ich opisów, zobacz [właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).

Jeśli test obciążenia zawiera tylko jeden węzeł Ustawienia uruchomieniowego w folderze **Parametry uruchomieniowe** , ten węzeł zawsze jest aktywnym węzłem. Jeśli test obciążenia zawiera wiele węzłów parametrów uruchomieniowych, można wybrać jeden do użycia podczas uruchamiania testu obciążenia. Zobacz [jak: dodać dodatkowe parametry uruchomieniowe do testu obciążenia](../test/how-to-add-additional-run-settings-to-a-load-test.md).

W **Edytor testu obciążeniowego** ustawienie aktywnego przebiegu jest identyfikowane za pomocą sufiksu "[Active]".

## <a name="select-the-active-run-setting"></a>Wybierz aktywne ustawienie uruchomieniowe

1. Otwórz test obciążenia.

2. Rozwiń folder **Parametry uruchomieniowe** .

3. Kliknij prawym przyciskiem myszy węzeł Ustawienia uruchamiania, który ma być aktywnym węzłem, a następnie wybierz pozycję **Ustaw jako aktywny**.

     W **teście obciążenia Edito** r, węzeł Ustawienia uruchamiania, którego to dotyczy, zostanie zaktualizowany przy użyciu sufiksu "[Active]".

     Wybrane ustawienie przebiegu zostanie uaktywnione i pozostaje aktywne do momentu wybrania innego ustawienia uruchomieniowego, które ma być aktywne.

> [!NOTE]
> Można zastąpić aktywne ustawienie uruchomieniowe, ustawiając zmienną środowiskową o nazwie `Test.UseRunSetting=<run setting name>` . Jest to przydatne w przypadku uruchamiania testu obciążenia z wiersza polecenia lub pliku wsadowego. Pozwala to wybrać różne Parametry uruchomieniowe bez otwierania testu obciążenia.

## <a name="specify-the-run-setting-to-use-from-the-command-line"></a>Określ ustawienie uruchomieniowe do użycia z wiersza polecenia

Można zastąpić domyślne parametry uruchomieniowe w teście obciążenia, ustawiając zmienną środowiskową z wiersza polecenia:

**Ustaw test. UseRunSetting = PreProdEnvironment**

I do uruchomienia testu:

**MSTest/testcontainer: LoadTest1. LoadTest**

## <a name="see-also"></a>Zobacz też

- [Skonfiguruj ustawienia przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
- [Określ zestawy liczników i reguły progowe dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Instrukcje: Dodawanie dodatkowych parametrów uruchomieniowych do testu obciążenia](../test/how-to-add-additional-run-settings-to-a-load-test.md)
