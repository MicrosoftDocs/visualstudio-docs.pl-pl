---
title: Określanie liczby iteracji testowych w ustawieniach uruchamiania testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: 6ef3b4197067b379343ea65eb39c734f0ce8916f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53903018"
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>Instrukcje: Określanie liczby iteracji testowych w teście obciążeniowym, ustawienia uruchamiania

Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążeniowego**, możesz użyć **edytora testu obciążenia** można zmienić właściwości scenariuszy do spełnienia potrzeb i celów testowania. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md).

Za pomocą **edytora testu obciążenia**, można edytować **iteracji testu** właściwości wartości parametrów uruchomieniowych w **właściwości** okna. **Iteracje testu** właściwość określa liczbę iteracji do uruchamiania na wszystkich sieci web wydajności i testy jednostkowe we wszystkich scenariuszach testów obciążenia przy użyciu **edytora testu obciążenia**.

> [!NOTE]
> Aby uzyskać pełną listę właściwości parametrów uruchomieniowych i ich opisów, zobacz [właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>Aby określić liczbę iteracji testowych w ustawieniach testu

1.  Otwórz test obciążenia.

     **Edytora testu obciążenia** pojawi się i wyświetli drzewa testu obciążenia.

2.  Obciążenia testowanie drzewa, w **parametrów uruchomieniowych** folderu, wybierz ustawienie uruchamiania.

3.  Na **widoku** menu, wybierz opcję **okno właściwości** do wyświetlania obciążenia Uruchom kategorii i właściwości tego ustawienia.

4.  Ustaw **Użyj iteracji testu** właściwości **True**.

5.  W **iteracje testu** właściwość, wprowadź numer, który wskazuje liczbę iteracji testu do uruchomienia podczas testu obciążeniowego.

6.  Po zakończeniu, zmiana wartości właściwości, wybierz **Zapisz** na **pliku** menu. Następnie możesz uruchomić test obciążenia za pomocą nowego **iteracje testu** wartość.

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)