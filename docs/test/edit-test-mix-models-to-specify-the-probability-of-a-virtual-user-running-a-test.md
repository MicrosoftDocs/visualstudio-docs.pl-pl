---
title: Edytowanie modeli miksowania tekstu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, virtual users
ms.assetid: e3b7d952-9012-400a-8131-3444390a6066
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 62c817a2df6c56f70ab2217292feeb545cf66c85
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593216"
---
# <a name="edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test"></a>Edytuj modele miksu testowego, aby określić prawdopodobieństwo uruchomienia testu przez użytkownika wirtualnego

*Model mix testu* określa prawdopodobieństwo użytkownika wirtualnego uruchomienie danego testu w scenariuszu testu obciążenia. Dzięki temu można symulować obciążenia bardziej realistycznie. Zamiast mieć tylko jeden przepływ pracy za pośrednictwem aplikacji, można mieć kilka przepływów pracy, co jest bliższe przybliżenie sposobu interakcji użytkowników końcowych z aplikacjami.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-options"></a>Testowanie opcji modelu mieszanek

Można określić jedną z następujących opcji modelu testu dla scenariusza testu obciążenia:

- **Na podstawie całkowitej liczby testów:** Określa, który test wydajności sieci web lub jednostki jest uruchamiany, gdy użytkownik wirtualny rozpoczyna iterację testową. Na końcu testu obciążenia liczba uruchomiono określony test jest zgodna z przypisanym rozkładem testu. Użyj tego modelu mix testu, gdy opierasz mix testu na procentach transakcji w dzienniku IIS lub w danych produkcyjnych.

- **Na podstawie liczby użytkowników wirtualnych:** Określa procent użytkowników wirtualnych, którzy będą uruchamiać określoną wydajność sieci web lub test jednostkowy. W dowolnym momencie testu obciążenia liczba użytkowników, którzy są uruchomione określonego testu odpowiada przypisanej dystrybucji. Użyj tego modelu mix testu, gdy są oparte mix testu na procent użytkowników korzystających z określonego testu.

- **Na podstawie tempa użytkownika:** W trakcie testu obciążenia każdy test wydajności sieci web lub test jednostkowy jest uruchamiany określoną liczbę razy na użytkowników na godzinę. Użyj tego modelu mix testu, jeśli chcesz, aby użytkownicy wirtualni uruchomić test w określonym tempie przez cały test obciążenia.

- **Na podstawie kolejności:** Każdy użytkownik wirtualny uruchamia wydajność sieci web lub testy jednostkowe w kolejności, w. Użytkownik wirtualny kontynuuje przechodzenie do pracy w tej kolejności podczas wykonywania testów w tej kolejności.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Określająca kombinację testów dla testu obciążenia:** Podczas tworzenia testu obciążenia należy określić ustawienia testu obciążenia w **Kreatorze nowego testu obciążenia**. W **Kreatorze nowego testu obciążenia**można wybrać istniejące testy sieci web i jednostkowe, które mają być dodane do początkowego scenariusza. Po dodaniu testów do scenariusza, należy określić mix testu dla scenariusza.<br /><br /> Opcje modelowania obciążenia służą do dokładniejszego przewidywania oczekiwanego rzeczywistego użycia witryny sieci Web lub aplikacji, które są testujące obciążenie. Jest to ważne, ponieważ test obciążenia, który nie jest oparty na modelu dokładnego obciążenia może generować mylące wyniki.|-   [Emulowanie oczekiwanego rzeczywistego korzystania ze strony internetowej lub aplikacji](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md)|
|**Edytuj model miksu testowego:** Można zmienić scenariusz testu obciążenia, aby użyć jednego z modeli mix testu przy użyciu **Edytora testów obciążenia**.||
|**Skonfiguruj opóźnienie tempa dla modelu miksu testowego według użytkownika:** Jeśli scenariusz testu obciążenia jest skonfigurowany do używania **modelu mix testu tempa użytkownika,** można określić sposób konfigurowania opóźnienia pacingu dystrybucji.|-   [Jak: Stosowanie dystrybucji do opóźnienia tempa podczas korzystania z modelu testu tempa użytkownika](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|

## <a name="change-the-test-mix-model-in-a-scenario"></a>Zmienianie modelu miksu testowego w scenariuszu

Po utworzeniu testu obciążenia przy użyciu **Kreatora nowego testu obciążenia**można użyć **Edytora testów obciążenia,** aby zmienić właściwości scenariuszy, aby spełnić twoje potrzeby i cele testowania.

> [!NOTE]
> Aby uzyskać pełną listę właściwości ustawień obciążenia i ich opisów, zobacz [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md).

Za pomocą **Edytora testów obciążenia**można zmienić model mix testu w scenariuszu testu obciążenia, edytując **Test Mix Type** właściwości w oknie **Właściwości.**

### <a name="to-change-the-test-mix-model"></a>Aby zmienić model miksu testowego

1. Otwórz test obciążenia.

     Pojawi się **Edytor testów obciążenia.** Zostanie wyświetlone drzewo testu obciążenia.

2. W *folderze Scenariusze* drzewa testów obciążenia wybierz węzeł scenariusza, dla którego chcesz określić maksymalną liczbę iteracji testowych.

3. W menu **Widok** wybierz polecenie **Okno Właściwości**.

     Wyświetlane są kategorie i właściwości scenariusza.

4. We właściwości **Test Mix Type** wybierz przycisk wielokropka ( **...**).

     Zostanie wyświetlone okno dialogowe **Edytowanie miksu testowego.**

5. Wybierz listę rozwijaną w obszarze **Test modelu mix** i wybierz model mix testu, który ma być używany w scenariuszu.

6. (Opcjonalnie) Zmodyfikuj kombinację testów za pomocą przycisków **Dodaj**, **Usuń** i **Rozmieść** i rozmieszczaj. Aby uzyskać więcej informacji, zobacz [Edytowanie zestawu testów, aby określić, które testy mają być uwzględnione w scenariuszu testu obciążenia.](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)

7. (Opcjonalnie) Określ wydajność sieci Web i test jednostkowy, aby zainicjować lub zakończyć za pomocą pól wyboru i wybierając żądane testy. Aby uzyskać więcej informacji, zobacz [Emulowanie oczekiwanego rzeczywistego użycia witryny sieci Web lub aplikacji](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md).

8. Wybierz pozycję **OK**.

     Okno **Właściwości** wyświetla nowy model mix testu dla **Test Mix Type** właściwości.

9. Po zmianie właściwości wybierz polecenie **Zapisz** w menu **Plik.** Następnie można uruchomić test obciążenia przy użyciu nowej wartości **test mix type.**

## <a name="see-also"></a>Zobacz też

- [Edytowanie scenariuszy testów obciążenia](../test/edit-load-test-scenarios.md)
- [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md)
