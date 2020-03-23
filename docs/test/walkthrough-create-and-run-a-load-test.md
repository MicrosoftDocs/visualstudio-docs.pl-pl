---
title: Tworzenie i uruchamianie testów obciążeniowych
ms.date: 10/01/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, in load tests
- unit tests, load test walkthrough
- load tests, walkthrough
ms.assetid: bbf075a5-96d5-48ed-a03c-330f0fc04748
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 780485a4d42cad574cddaaa5a9ae51a65a1a9b7d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093629"
---
# <a name="walkthrough-create-and-run-a-load-test-that-contains-unit-tests"></a>Instruktaż: Tworzenie i uruchamianie testu obciążenia zawierającego testy jednostkowe

W tym instruktażu można utworzyć test obciążenia, który zawiera testy jednostkowe.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

W tym przewodniku kroki podczas tworzenia, a następnie uruchamianie testu obciążenia przy użyciu programu Visual Studio Enterprise. Test obciążenia jest kontenerem testów wydajności sieci web i testów jednostkowych. Testy obciążenia są tworzą za pomocą **Kreatora nowego testu obciążenia**.

Test obciążenia udostępnia również wiele właściwości w czasie wykonywania, które można zmodyfikować w celu wygenerowania symulacji żądanego obciążenia. W tym instruktażu można użyć **Kreatora nowego testu obciążenia,** aby dodać testy jednostkowe do testu obciążenia.

W tym instruktażu wykonasz następujące zadania:

- Utwórz test obciążenia, który używa testów jednostkowych.

- Zmień niektóre ustawienia testu obciążenia.

- Uruchom test obciążenia.

- Wykonaj kroki opisane w [przewodniku: Tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) w celu utworzenia prostej biblioteki klas języka C#, która zawiera projekt testu wydajności sieci web i obciążenia z niektórymi testami jednostkowymi.

## <a name="create-a-load-test-containing-unit-tests-using-the-new-load-test-wizard"></a>Tworzenie testu obciążenia zawierającego testy jednostkowe za pomocą Kreatora nowego testu obciążenia

### <a name="to-start-the-new-load-test-wizard"></a>Aby uruchomić Kreatora nowego testu obciążenia

1. Upewnij się, że zainstalowano składnik **narzędzi do testowania wydajności sieci Web i testowania obciążenia** opisany w części Tworzenie projektu testu [obciążenia](../test/quickstart-create-a-load-test-project.md).

1. Otwórz rozwiązanie Bank utworzone w [przewodniku: Tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).

1. W **Eksploratorze rozwiązań**otwórz menu skrótów dla węzła Rozwiązanie Bank, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **Nowy projekt**.

     Zostanie wyświetlone okno dialogowe **Dodawanie nowego projektu.**

1. W oknie dialogowym **Dodawanie nowego projektu** rozwiń węzeł Visual **C#** i wybierz pozycję **Testuj**. Z listy szablonów wybierz pozycję **Projekt testu wydajności sieci Web i testu obciążenia** oraz w polu **Nazwa** wpisz . `BankLoadTest` Wybierz pozycję **OK**.

     Projekt testu wydajności i testu obciążenia w sieci Web BankLoadTest jest dodawany do rozwiązania.

1. Otwórz menu skrótów dla nowego projektu testu wydajności i ładowania konta BankLoadTest, wybierz pozycję **Dodaj**, a następnie wybierz polecenie **Testuj obciążenie**.

1. Zostanie uruchomiony **Kreator nowego testu obciążenia.**

1. Strona **powitalna** **Kreatora nowego testu obciążenia** jest pierwszą stroną.

1. Wybierz pozycję **Dalej**.

### <a name="to-edit-settings-for-load-test-scenario"></a>Aby edytować ustawienia dla scenariusza testu obciążenia

1. W polu **tekstowym Wprowadź nazwę scenariusza testu obciążenia** wpisz **ScenarioSample**.

     *Scenariusz* jest mechanizmem grupowania. Składa się z zestawu testów i właściwości do uruchamiania tych testów pod obciążeniem.

2. Ustaw **profil czasu** `Use normal distribution centered on recorded think times`Think to . Czasy zastanowienia reprezentują czas, w który użytkownik rozważałby stronę internetową przed przejściem do następnej strony.

1. Po zakończeniu wybierz pozycję **Dalej.**

### <a name="to-edit-load-pattern-setting-for-test-scenario"></a>Aby edytować ustawienie wzorca obciążenia dla scenariusza testowego

1. Wybierz **polecenie Obciążenie krokowe**.

    > [!NOTE]
    > Można wybrać jeden z dwóch typów wzorców obciążenia: stały i krokowy. Każdy typ ma swoją funkcję w testowaniu obciążenia, ale na potrzeby tego przewodnika wybierz **krok obciążenia**.

2. Ustaw **liczbę użytkowników startowych** na 10 użytkowników.

3. Ustaw **czas trwania kroku** na 10 sekund.

4. Ustaw **liczbę użytkowników kroku** na 10 użytkowników/krok.

5. Ustaw **maksymalną liczbę użytkowników** na 100 użytkowników.

6. Wybierz pozycję **Dalej**.

### <a name="to-select-test-mix-model-for-the-scenario"></a>Aby wybrać model testu mix dla scenariusza

1. W obszarze **Jak należy modelować mieszankę testów**, wybierz na **podstawie całkowitej liczby testu**.

2. Wybierz pozycję **Dalej**.

### <a name="to-add-unit-tests-to-the-scenario"></a>Aby dodać testy jednostkowe do scenariusza

1. Następnym krokiem jest **dodanie testów do scenariusza testu obciążenia i edycji testu mix**.

2. Wybierz **pozycję Dodaj,** aby wybrać testy.

3. Wybierz testy jednostkowe **CreditTest** wymienione w okienku **Dostępne testy,** które zawiera listę wszystkich testów wydajności sieci Web i testów jednostkowych w projekcie testu wydajności sieci Web i obciążenia.

4. Wybierz strzałkę, aby dodać test jednostkowy **CreditTest** do okienka **Wybrane testy.**

5. Powtórz kroki 3 i 4 dla **debittest** i **FreezeAccountTest** testów jednostkowych.

6. Po zakończeniu dodawania trzech testów jednostkowych wybierz przycisk **OK**.

     Zostanie wyświetlona mieszanka testowa.

7. Przesuń suwak w obszarze **Dystrybucja** dla **CreditTest** nieznacznie w prawo, aby dostosować dystrybucję testów. Należy zauważyć, że inne suwaki przesuwają się automatycznie w lewo, tak aby rozkład pozostał na poziomie 100%.

8. Wybierz pozycję **Dalej**.

### <a name="to-select-network-mix-for-test-scenario"></a>Aby wybrać kombinację sieci dla scenariusza testowego

1. Wybierz typ połączenia SIECI LAN, który ma być dodawany do koszyka przepustowości sieci.

     Można dodać więcej typów sieci. Użyj suwaków, aby dostosować rozkład testu i ważenie.

2. Wybierz pozycję **Dalej**.

### <a name="to-specify-computers-to-monitor-with-counter-sets-during-load-test-run"></a>Aby określić komputery do monitorowania z zestawami liczników podczas przebiegu testu obciążenia

1. Wybierz pozycję **Dalej**.

     Aby uzyskać więcej informacji na temat zestawów liczników, zobacz [Określanie zestawów liczników i reguł progowych dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

### <a name="to-edit-run-setting-for-load-test"></a>Aby edytować ustawienie uruchamiania dla testu obciążenia

1. Wybierz **czas trwania testu obciążenia,** a następnie ustaw czas trwania **uruchomienia** do 2 minut, aby sprawdzić *obciążenie dymem.*

     Podczas tworzenia testów obciążenia, jest dobrą praktyką, aby sprawdzić, czy wszystko jest poprawnie skonfigurowane i działa zgodnie z oczekiwaniami, uruchamiając krótki, lekki test obciążenia. Proces ten jest znany jako *badanie dymu*.

2. Wybierz **pozycję Zakończ**. Test obciążenia jest otwarty w **Edytorze testów obciążenia**.

## <a name="run-the-load-test"></a>Uruchom test obciążenia
 Po utworzeniu testu obciążenia uruchom go, aby wyświetlić, jak aplikacja bankowa reaguje na symulację obciążenia. Gdy test obciążenia jest uruchomiony, zostanie wyświetle okno **Analizator testu obciążenia.**

### <a name="to-run-the-load-test"></a>Aby uruchomić test obciążenia

1. Po otwarciu testu obciążenia w **Edytorze testów obciążenia**wybierz zielony przycisk **Uruchom test** na pasku narzędzi. Rozpocznie się ładowanie testu.

2. Jeśli symulacja testu przekracza wszelkie progi, ikony pojawiają się w węzłach kontroli drzewa, aby wskazać naruszenie progu. Błędy mają nakładkę na czerwone kółko, ostrzeżenia mają żółtą nakładkę trójkąta. Można znaleźć licznik, który przekroczył próg i wykres go przeciągając ikonę na wykresie. Można to zrobić, gdy test jest uruchomiony.

## <a name="see-also"></a>Zobacz też

- [Edytuj kombinację testów, aby określić, które testy mają być uwzględniane w scenariuszu testu obciążenia](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Określanie typów sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md)
- [Edytowanie scenariuszy testów obciążenia](../test/edit-load-test-scenarios.md)
- [Edytowanie wzorców obciążenia w celu modelowania działań użytkownika wirtualnego](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Edytowanie modeli mieszania tekstu w celu określenia prawdopodobieństwa uruchomienia testu przez użytkownika wirtualnego](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
