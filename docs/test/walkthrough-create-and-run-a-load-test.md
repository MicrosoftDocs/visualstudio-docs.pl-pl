---
title: Tworzenie i uruchamianie testów obciążeniowych
description: Dowiedz się, jak utworzyć test obciążenia, który zawiera testy jednostkowe. Możesz tworzyć i uruchamiać testy obciążenia przy użyciu Visual Studio Enterprise.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: bdcd96e8fc87a7627689af1c67a81b69b2ecee72
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598266"
---
# <a name="walkthrough-create-and-run-a-load-test-that-contains-unit-tests"></a>Przewodnik: Tworzenie i uruchamianie testu obciążenia zawierającego testy jednostkowe

W tym instruktażu utworzysz test obciążenia, który zawiera testy jednostkowe.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Ten Instruktaż przeprowadzi Cię przez proces tworzenia i uruchamiania testu obciążenia przy użyciu Visual Studio Enterprise. Test obciążenia jest kontenerem testów wydajności sieci Web i testów jednostkowych. Możesz tworzyć testy obciążenia z **nowym Kreator testu obciążeniowego**.

Test obciążenia ujawnia również wiele właściwości czasu wykonywania, które można zmodyfikować, aby wygenerować pożądaną symulację obciążenia. W tym instruktażu użyjemy **nowego Kreator testu obciążeniowego** , aby dodać testy jednostkowe do testu obciążenia.

W tym instruktażu wykonasz następujące zadania:

- Utwórz test obciążenia, który korzysta z testów jednostkowych.

- Zmień niektóre ustawienia testu obciążenia.

- Uruchom test obciążenia.

- Wykonaj kroki opisane w [przewodniku: Tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) w celu utworzenia prostej biblioteki klas języka C#, która zawiera projekt testów wydajności sieci Web i obciążenia z pewnymi testami jednostkowymi.

## <a name="create-a-load-test-containing-unit-tests-using-the-new-load-test-wizard"></a>Utwórz test obciążenia zawierający testy jednostkowe przy użyciu nowego Kreator testu obciążeniowego

### <a name="to-start-the-new-load-test-wizard"></a>Aby rozpocząć nowe Kreator testu obciążeniowego

1. Upewnij się, że zainstalowano składnik **narzędzi do testowania wydajności sieci Web i testów obciążenia** opisany w artykule [Tworzenie projektu testu obciążenia](../test/quickstart-create-a-load-test-project.md).

1. Otwórz rozwiązanie bankowe, które zostało utworzone w [przewodniku: Tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).

1. W **Eksplorator rozwiązań** Otwórz menu skrótów dla węzła rozwiązanie banku, wybierz **Dodaj**, a następnie wybierz **Nowy projekt**.

     Zostanie wyświetlone okno dialogowe **Dodaj nowy projekt** .

1. W oknie dialogowym **Dodaj nowy projekt** rozwiń pozycję **Visual C#** , a następnie wybierz pozycję **Testuj**. Z listy szablonów wybierz **projekt test wydajności i obciążenia sieci Web** , a w polu **Nazwa** wpisz `BankLoadTest` . Wybierz przycisk **OK**.

     Projekt testu wydajności i obciążenia sieci Web BankLoadTest jest dodawany do rozwiązania.

1. Otwórz menu skrótów dla nowego projektu test wydajności i obciążenia sieci Web BankLoadTest, wybierz polecenie **Dodaj**, a następnie wybierz polecenie **test obciążenia**.

1. Zostanie uruchomiony **nowy Kreator testu obciążeniowego** .

1. Na stronie **powitalnej** **nowej Kreator testu obciążeniowego** jest pierwsza strona.

1. Wybierz pozycję **Next** (Dalej).

### <a name="to-edit-settings-for-load-test-scenario"></a>Aby edytować ustawienia scenariusza testu obciążenia

1. W polu tekstowym **Wprowadź nazwę dla scenariusza testu obciążenia** wpisz **ScenarioSample**.

     *Scenariusz* jest mechanizmem grupowania. Składa się z zestawu testów i właściwości do uruchamiania tych testów w ramach obciążenia.

2. Ustaw profil czasu, na który **sądzisz** `Use normal distribution centered on recorded think times` . Czasy reakcji reprezentują czas, jaki użytkownik mógłby spędzać stronie sieci Web przed przejściem do następnej strony.

1. Po zakończeniu wybierz pozycję **dalej** .

### <a name="to-edit-load-pattern-setting-for-test-scenario"></a>Aby edytować ustawienia wzorca obciążenia dla scenariusza testu

1. Wybierz pozycję **Załaduj krok**.

    > [!NOTE]
    > Można wybrać jedną z dwóch typów wzorców obciążenia: stała i krok. Każdy typ ma swoją funkcję w testowaniu obciążenia, ale na potrzeby tego instruktażu wybierz opcję **obciążenie etapem**.

2. Ustaw wartość **początkowa liczba** użytkowników na 10 użytkowników.

3. Ustaw **czas trwania kroku** na 10 sekund.

4. Ustaw **liczbę użytkowników kroku** na wartość 10 users/krok.

5. Ustaw **maksymalną liczbę** użytkowników na 100.

6. Wybierz pozycję **Next** (Dalej).

### <a name="to-select-test-mix-model-for-the-scenario"></a>Aby wybrać model testu mieszanego dla scenariusza

1. W obszarze **jak należy modelować test mieszany**, zaznacz **w oparciu o łączną liczbę testów**.

2. Wybierz pozycję **Next** (Dalej).

### <a name="to-add-unit-tests-to-the-scenario"></a>Aby dodać testy jednostkowe do scenariusza

1. Następnym krokiem jest **dodanie testów do scenariusza testu obciążenia i edycja testu mieszanego**.

2. Wybierz pozycję **Dodaj** , aby wybrać testy.

3. Wybierz testy jednostkowe **CreditTest** wymienione w okienku **dostępne testy** , które wyświetla listę wszystkich testów wydajności sieci Web i testów jednostkowych w projekcie testu wydajności i obciążenia sieci Web.

4. Wybierz strzałkę, aby dodać test jednostkowy **CreditTest** do okienka **Wybrane testy** .

5. Powtórz kroki 3 i 4 dla testów jednostkowych **DebitTest** i **FreezeAccountTest** .

6. Po zakończeniu dodawania trzech testów jednostkowych wybierz **przycisk OK**.

     Zostanie wyświetlony test mieszany.

7. Przesuń suwak w obszarze **dystrybucja** dla **CreditTest** nieco w prawo, aby dostosować dystrybucję testu. Zwróć uwagę, że inne suwaki są automatycznie przenoszone w lewo, aby dystrybucja pozostała w wysokości 100%.

8. Wybierz pozycję **Next** (Dalej).

### <a name="to-select-network-mix-for-test-scenario"></a>Aby wybrać opcję mieszanie sieci dla scenariusza testowego

1. Wybierz typ połączenia sieci LAN, który ma zostać dodany do mieszanej przepustowości sieci.

     Możesz dodać więcej typów sieci. Użyj suwaków, aby dostosować dystrybucję testu i ważenie.

2. Wybierz pozycję **Next** (Dalej).

### <a name="to-specify-computers-to-monitor-with-counter-sets-during-load-test-run"></a>Aby określić komputery, które mają być monitorowane przy użyciu zestawów liczników podczas przebiegu testu obciążenia

1. Wybierz pozycję **Next** (Dalej).

     Aby uzyskać więcej informacji na temat zestawów liczników, zobacz [Określanie zestawów liczników i reguł progu dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

### <a name="to-edit-run-setting-for-load-test"></a>Aby edytować ustawienie uruchomieniowe testu obciążenia

1. Wybierz pozycję **czas trwania testu obciążenia** , a następnie ustaw **czas trwania** na 2 minuty w celu *przetestowania* testu obciążenia przez program dymu.

     Podczas kompilowania testów obciążenia warto sprawdzić, czy wszystko jest poprawnie skonfigurowane i działa zgodnie z oczekiwaniami, uruchamiając krótki, lekki test obciążenia. Ten proces jest nazywany *testowaniem dymu*.

2. Wybierz pozycję **Zakończ**. Test obciążenia zostanie otwarty w **Edytor testu obciążeniowego**.

## <a name="run-the-load-test"></a>Uruchom test obciążenia
 Po utworzeniu testu obciążenia, uruchom go, aby zobaczyć, jak Twoja aplikacja bankowa odpowiada na symulację obciążenia. Gdy test obciążenia jest uruchomiony, zobaczysz okno **Analizator testu obciążenia** .

### <a name="to-run-the-load-test"></a>Aby uruchomić test obciążenia

1. Przy otwartym teście obciążenia w **Edytor testu obciążeniowego** wybierz przycisk zielony **przebieg testu** na pasku narzędzi. Test obciążenia rozpocznie się.

2. Jeśli symulacja testowa przekracza wartości progowe, ikony są wyświetlane w węzłach kontrolki drzewa, aby wskazać naruszenie progu. Błędy mają czerwoną nakładkę koła, ostrzeżenia mają żółty trójkąt nakładki. Można znaleźć licznik, który przekroczył próg i przedstawić go na wykresie, przeciągając ikonę na Graf. Można to zrobić, gdy test jest uruchomiony.

## <a name="see-also"></a>Zobacz także

- [Edytuj mieszany test, aby określić, które testy należy uwzględnić w scenariuszu testu obciążenia](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Określanie typów sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md)
- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Edytuj wzorce obciążenia, aby modelować działania użytkownika wirtualnego](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Edytuj modele mieszane tekstu, aby określić prawdopodobieństwo uruchomienia testu przez użytkownika wirtualnego](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
