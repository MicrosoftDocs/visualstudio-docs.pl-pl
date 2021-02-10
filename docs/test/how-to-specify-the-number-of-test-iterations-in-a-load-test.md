---
title: Określ liczbę iteracji w ustawieniu przebiegu testu obciążenia
description: Dowiedz się, jak określić liczbę iteracji do uruchomienia na wszystkich testach wydajności sieci Web i testów jednostkowych we wszystkich scenariuszach w teście obciążenia przy użyciu Edytor testu obciążeniowego.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: a257b5800166e840194a28cba0ca99849b05f579
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936200"
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>Instrukcje: Określanie liczby iteracji testowych w ustawieniu przebiegu testu obciążenia

Po utworzeniu testu obciążenia przy użyciu **nowego Kreator testu obciążeniowego** można użyć **Edytor testu obciążeniowego** , aby zmienić właściwości scenariuszy, aby spełniały potrzeby testowania i cele. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md).

Za pomocą **Edytor testu obciążeniowego** można edytować Właściwość **iteracje testu** wartości parametrów uruchomieniowych w oknie **Właściwości** . Właściwość **iteracje testu** określa liczbę iteracji do uruchomienia na wszystkich testach wydajności sieci Web i testów jednostkowych we wszystkich scenariuszach w teście obciążenia przy użyciu **Edytor testu obciążeniowego**.

> [!NOTE]
> Aby uzyskać pełną listę właściwości parametrów uruchomieniowych i ich opisów, zobacz [właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>Aby określić liczbę iteracji testowych w ustawieniu uruchomieniowym

1. Otwórz test obciążenia.

     Zostanie wyświetlone **Edytor testu obciążeniowego** i zostanie wyświetlone drzewo testów obciążenia.

2. W drzewie testu obciążenia w folderze **Parametry uruchomieniowe** wybierz ustawienie Uruchom.

3. W menu **Widok** wybierz pozycję **okno właściwości** , aby wyświetlić kategorie i właściwości ustawienia przebiegu ładowania.

4. Ustaw dla właściwości **Użyj iteracji testu** **wartość true**.

5. We właściwości **iteracje testu** wprowadź liczbę, która wskazuje liczbę iteracji testowych do uruchomienia podczas testu obciążenia.

6. Po zakończeniu zmiany właściwości wybierz pozycję **Zapisz** w menu **plik** . Następnie można uruchomić test obciążenia przy użyciu nowych wartości **iteracji testu** .

## <a name="see-also"></a>Zobacz też

- [Skonfiguruj ustawienia przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
- [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md)
