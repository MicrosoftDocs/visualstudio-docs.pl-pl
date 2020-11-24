---
title: Edytowanie modeli tekstu mieszanego
description: Dowiedz się, w jaki sposób model testu mieszanego pozwala na korzystanie z kilku przepływów pracy, co jest bardziej ściśle zbliżone do sposobu, w jaki użytkownicy końcowi pracują z aplikacjami.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios
- load tests, virtual users
ms.assetid: e3b7d952-9012-400a-8131-3444390a6066
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0d95eee8dd4e49e74b9bafd048e3f672fe560c68
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441368"
---
# <a name="edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test"></a>Edytuj modele testów mieszanych, aby określić prawdopodobieństwo uruchomienia testu przez użytkownika wirtualnego

*Model testu mieszanego* określa prawdopodobieństwo, że użytkownik wirtualny uruchamia dany test w scenariuszu testu obciążenia. Pozwala to bardziej realistycznie symulować obciążenie. Zamiast mieć tylko jeden przepływ pracy za pomocą aplikacji, można korzystać z kilku przepływów pracy, co jest bliższe przybliżenie, w jaki sposób użytkownicy końcowi współpracują z aplikacjami.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-options"></a>Opcje modelu testu mieszanego

Możesz określić jedną z następujących opcji modelu testu mieszanego dla scenariusza testu obciążenia:

- **W oparciu o łączną liczbę testów:** Określa, który test wydajności sieci Web lub testy jednostkowe są uruchamiane, gdy użytkownik wirtualny rozpocznie iterację testową. Po zakończeniu testu obciążenia, liczba uruchomień określonego testu jest zgodna z przypisaną dystrybucją testu. Ten model testu mieszanego jest używany, gdy bazowasz test mieszany dla procentu transakcji w dzienniku IIS lub w danych produkcyjnych.

- **Na podstawie liczby wirtualnych użytkowników:** Określa wartość procentową użytkowników wirtualnych, którzy będą uruchamiać określony test wydajności sieci Web lub testy jednostkowe. W każdym punkcie testu obciążenia liczba użytkowników, którzy uruchamiali określony test, odpowiada przypisanej dystrybucji. Użyj tego modelu testu mieszanego, gdy tworzysz test mieszany dla procentu użytkowników, którzy uruchamiają określony test.

- **Na podstawie tempa użytkownika:** W trakcie testu obciążenia każdy test wydajności sieci Web lub test jednostkowy jest uruchamiany określoną liczbę razy dla poszczególnych użytkowników na godzinę. Użyj tego modelu testu mieszanego, jeśli chcesz, aby użytkownicy wirtualną uruchamiali test w pewnym tempie w trakcie testu obciążenia.

- **W oparciu o kolejność sekwencyjną:** Każdy użytkownik wirtualny uruchamia testy wydajności sieci Web lub testów jednostkowych w kolejności, w której testy są zdefiniowane w scenariuszu. Użytkownik wirtualny kontynuuje przechodzenie przez testy w tej kolejności do momentu zakończenia testu obciążenia.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Określanie mieszanki testowej dla testu obciążenia:** Podczas tworzenia testu obciążenia należy określić ustawienia testu obciążenia w **nowym Kreator testu obciążeniowego**. W **nowych Kreator testu obciążeniowego** wybierasz istniejące testy sieci Web i jednostek, aby dodać je do scenariusza początkowego. Po dodaniu testów do scenariusza należy określić test mieszany dla scenariusza.<br /><br /> Opcja Załaduj model umożliwia dokładniejsze przewidywalność rzeczywistego użycia witryny sieci Web lub aplikacji, które są testowane. Należy to zrobić, ponieważ test obciążenia, który nie jest oparty na precyzyjnym modelu obciążenia, może generować błędne wyniki.|-   [Emulowanie oczekiwanego użycia witryny sieci Web lub aplikacji w świecie rzeczywistym](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md)|
|**Edytuj model testu mieszanego:** Można zmienić scenariusz testu obciążenia, aby użyć jednego z modeli testów mieszanych za pomocą **Edytor testu obciążeniowego**.||
|**Skonfiguruj opóźnienie tempem dla modelu testowego:** Jeśli scenariusz testu obciążenia jest skonfigurowany do korzystania z **modelu standardu testowego**, możesz określić sposób, w jaki ma zostać skonfigurowane opóźnienie tempem.|-   [Instrukcje: stosowanie dystrybucji do opóźnień tempem w przypadku korzystania z modelu mieszanego testów](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|

## <a name="change-the-test-mix-model-in-a-scenario"></a>Zmiana modelu testu mieszanego w scenariuszu

Po utworzeniu testu obciążenia przy użyciu **nowego Kreator testu obciążeniowego** można użyć **Edytor testu obciążeniowego** , aby zmienić właściwości scenariuszy, aby spełniały potrzeby testowania i cele.

> [!NOTE]
> Aby uzyskać pełną listę właściwości ustawień ładowania i ich opisów, zobacz [właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md).

Za pomocą **Edytor testu obciążeniowego** można zmienić model testu mieszanego w scenariuszu testu obciążenia, edytując Właściwość **test mix Type** w oknie **Właściwości** .

### <a name="to-change-the-test-mix-model"></a>Aby zmienić model testu mieszanego

1. Otwórz test obciążenia.

     Zostanie wyświetlona **Edytor testu obciążeniowego** . Zostanie wyświetlone drzewo testu obciążenia.

2. W folderze *scenariusze* drzewa testu obciążenia wybierz węzeł scenariusza, dla którego chcesz określić maksymalną liczbę iteracji testowych.

3. W menu **Widok** wybierz polecenie **okno właściwości**.

     Wyświetlane są kategorie i właściwości scenariusza.

4. We właściwości **typ testu mieszanego** wybierz przycisk wielokropka ( **...**).

     Zostanie wyświetlone okno dialogowe **Edytowanie testu mieszanego** .

5. Wybierz listę rozwijaną w obszarze **model testu mieszanego** , a następnie wybierz model testu mieszanego, który ma być używany w tym scenariuszu.

6. Obowiązkowe Zmodyfikuj mieszany test, używając przycisków **Dodaj**, **Usuń** i **Dystrybuuj** oraz suwaków dystrybucji. Aby uzyskać więcej informacji, zobacz [Edytuj test mieszany, aby określić, które testy należy uwzględnić w scenariuszu testu obciążenia](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

7. Obowiązkowe Określ wydajność sieci Web i test jednostkowy do zainicjowania lub zakończenia przy użyciu pól wyboru i wybierania żądanych testów. Aby uzyskać więcej informacji, zobacz [emulacja oczekiwanego użycia witryny sieci Web lub aplikacji w świecie rzeczywistym](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md).

8. Wybierz przycisk **OK**.

     W oknie **Właściwości** zostanie wyświetlony nowy model testu mieszanego dla właściwości **typ testu mieszanego** .

9. Po zmianie właściwości wybierz pozycję **Zapisz** w menu **plik** . Następnie można uruchomić test obciążenia za pomocą nowej wartości **typ testu mieszanego** .

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md)
