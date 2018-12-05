---
title: Edytowanie modeli testów mieszanych w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, virtual users
ms.assetid: e3b7d952-9012-400a-8131-3444390a6066
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: acb786a4182a79a4133e2d94000ab5f7693bade3
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894667"
---
# <a name="edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test"></a>Edytowanie modeli testów mieszanych, aby określić prawdopodobieństwo, że użytkownik wirtualny uruchomi testu

*Model testu mieszanego* określa prawdopodobieństwo, że użytkownik wirtualny uruchomi dany test w scenariuszu testu obciążenia. Dzięki temu można bardziej realistycznie symulowanie obciążenia. Zamiast tylko jedego przepływu pracy za pośrednictwem aplikacji, może mieć wiele przepływów pracy, który jest większym zbliżeniem tego jak użytkownicy końcowi są wzajemne powiązani ze swoimi aplikacjami.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-options"></a>Opcje modelu mieszanego testu

Można określić jedną z następujących opcji model testu mieszanego, dla scenariusza testu obciążenia:

-   **Na podstawie całkowitej liczby testów:** Określa, który test wydajności lub jednostki w sieci web jest uruchamiany, gdy wirtualny użytkownik rozpoczyna iterację testu. Na koniec testu obciążenia liczby uruchamianych konkretnego testu pasuje dystrybucji przypisanych testu. Ten model testu mieszanego należy użyć, gdy test mieszany jest tworzony na transakcji, określonym w dzienniku IIS lub w danych produkcyjnych.

-   **Na podstawie liczby użytkowników wirtualnych:** Określa procent wirtualnych użytkowników, którzy uruchomią namierzenie internetowego testu wydajności lub jednostki. W dowolnym momencie testu obciążeniowego liczbę użytkowników, którzy uruchomili określonego testu pasuje do przypisanego rozkładu. Ten model testu mieszanego należy użyć, gdy test mieszany jest bazowanie na procencie użytkowników określonego testu.

-   **Na podstawie tempa użytkownika:** czasie trwania testu obciążeniowego każdy test wydajności sieci web lub test jednostkowy jest uruchamiany określoną liczbę razy na użytkowników, na godzinę. Ten model testu mieszanego należy użyć, jeśli chcesz, aby wirtualni użytkownicy uruchamiali test w konkretnym tempie przez cały test obciążeniowy.

-   **Na podstawie w kolejności sekwencyjnej:** każdy wirtualny użytkownik uruchamia testy wydajności lub jednostki sieci web w kolejności, że testy są zdefiniowane w tym scenariuszu. Wirtualny użytkownik kontynuuje, okrągło testów w następującej kolejności do czasu ukończenia testu obciążeniowego.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Określanie testu mieszanego dla testu obciążeniowego:** podczas tworzenia testu obciążeniowego można określić ustawień dla testu obciążenia w **Kreatora nowego testu obciążeniowego**. W **nowego kreatora testu obciążenia**, możesz wybrać istniejące sieci web i testy jednostkowe można dodać do scenariusza początkowej. Po dodaniu testy do scenariusza, należy określić test mieszany w scenariuszu.<br /><br /> Załaduj opcje modelowania umożliwia bardziej dokładnie przewidzieć oczekiwane wykorzystanie w świecie rzeczywistym witryny sieci Web lub aplikacji, które obciążenia testujesz. Należy to zrobić, ponieważ test obciążenia, który nie jest oparty na dokładne ładowanie modelu można wygenerować wyświetlenie nieprawdziwych wyników.|-   [Emulowanie oczekiwanego wykorzystania rzeczywistych witryny sieci Web lub aplikacji](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md)|
|**Edytuj model testu mieszanego:** można zmienić scenariusza testu obciążeniowego, aby użyć jednego z modeli testów mieszanych przy użyciu **edytora testu obciążenia**.||
|**Konfigurowanie rozkład opóźnienia dla użytkownika realizowany testu mieszanego modelu:** Jeśli scenariusza testu obciążenia jest skonfigurowany do używania **oparty na tempie model testu mieszanego użytkownika**, można określić sposób dystrybucji opóźnienie Pacing skonfigurowane.|-   [Porady: Zastosuj rozkład opóźnienia, korzystając z tempa model testu mieszanego użytkownika do](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|

## <a name="change-the-test-mix-model-in-a-scenario"></a>Zmień model testu mieszanego w scenariuszu

Po utworzeniu testu obciążenia przy użyciu **Kreatora nowego testu obciążeniowego**, możesz użyć **edytora testu obciążenia** można zmienić właściwości scenariuszy do spełnienia potrzeb i celów testowania.

> [!NOTE]
> Aby uzyskać pełną listę właściwości ustawień ładowania i ich opisów, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

Za pomocą **edytora testu obciążenia**, model testu mieszanego w scenariuszu testu obciążenia można zmienić, edytując **typ testu mieszanego** właściwość **właściwości** okna.

### <a name="to-change-the-test-mix-model"></a>Aby zmienić model testu mieszanego

1.  Otwórz test obciążenia.

     **Edytora testu obciążenia** pojawia się. Zostanie wyświetlone drzewo testu obciążenia.

2.  W *scenariuszy* folderu drzewa testu obciążenia, wybierz węzeł scenariusz, dla którego chcesz określić maksymalną liczbę iteracji testu.

3.  Na **widoku** menu, wybierz opcję **okno właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane.

4.  W **typ testu mieszanego** właściwości, wybierz przycisk wielokropka ( **...** ).

     **Edytuj Test mieszany** zostanie wyświetlone okno dialogowe.

5.  Wybierz z listy rozwijanej w obszarze **model testu mieszanego** i wybierz model testu mieszanego, za pomocą którego chcesz użyć dla tego scenariusza.

6.  (Opcjonalnie) Modyfikowanie mieszanki testów za pomocą **Dodaj**, **Usuń** i **dystrybucji** suwaki dystrybucji i przyciski. Aby uzyskać więcej informacji, zobacz [Edytuj test mieszany, aby określić, które testy, aby uwzględnić w scenariuszu testu obciążenia](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

7.  (Opcjonalnie) Określ testu sieci web wydajności i jednostki do inicjowania lub zakończenia, za pomocą pola wyboru i wybierając odpowiednią testów. Aby uzyskać więcej informacji, zobacz [Emulate oczekiwane wykorzystanie w świecie rzeczywistym witryny sieci Web lub aplikacji](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md).

8.  Wybierz **OK**.

     **Właściwości** okno wyświetla nowy model mieszaniny testu dla **typ testu mieszanego** właściwości.

9. Po zmianie właściwości wybierz **Zapisz** na **pliku** menu. Następnie można uruchomić testu obciążenia za pomocą nowego **typ testu mieszanego** wartość.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)