---
title: Tworzenie i uruchamianie testów obciążeniowych
ms.date: 10/01/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, in load tests
- unit tests, load test walkthrough
- load tests, walkthrough
ms.assetid: bbf075a5-96d5-48ed-a03c-330f0fc04748
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a319181348f86ab8f16b2cc2b7e9a6e6f3a16c13
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976264"
---
# <a name="walkthrough-create-and-run-a-load-test-that-contains-unit-tests"></a>Przewodnik: Tworzenie i uruchamianie testu obciążenia, który zawiera testy jednostkowe

W tym instruktażu utworzysz testu obciążenia, który zawiera testy jednostkowe.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Ten instruktaż prowadzi przez tworzenie, a następnie ponownie uruchomić test obciążenia przy użyciu programu Visual Studio Enterprise. Test obciążenia jest kontenerem testów wydajności sieci web i testów jednostkowych. Tworzenie testów obciążenia za pomocą **nowego kreatora testu obciążenia**.

Test obciążenia udostępnia również wiele właściwości czasu wykonywania, które można modyfikować, aby wygenerować pożądaną symulację obciążenia. W tym przewodniku używamy **Kreatora nowego testu obciążeniowego** Aby dodać testy jednostkowe do testu obciążenia.

W tym instruktażu wykonasz następujące zadania:

- Tworzenie testu obciążenia, który używa testów jednostkowych.

- Zmiana niektórych ustawień testu obciążenia.

- Uruchom test obciążenia.

- Wykonaj kroki opisane w [instruktażu: Tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) do utworzenia prostej C# biblioteki klasy, która zawiera web wydajności i obciążenia projektu testowego z niektórych jednostek testów w nim.

## <a name="create-a-load-test-containing-unit-tests-using-the-new-load-test-wizard"></a>Tworzenie testu obciążenia zawierającego testy jednostkowe za pomocą Kreatora nowego testu obciążeniowego

### <a name="to-start-the-new-load-test-wizard"></a>Aby uruchomić Kreatora nowego testu obciążenia

1. Otwórz rozwiązanie Bank, który został utworzony w [instruktażu: Tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).

2. W **Eksploratora rozwiązań**, otwórz menu skrótów dla węzła rozwiązanie Bank, wybierz pozycję **Dodaj**, a następnie wybierz **nowy projekt**.

     **Dodaj nowy projekt** Wyświetla okno dialogowe.

3. W **Dodaj nowy projekt** okna dialogowego rozwiń **Visual C#** i wybierz polecenie **testu**. Z listy szablonów wybierz **projekt testu obciążenia i wydajności sieci Web** i **nazwa** wpisz `BankLoadTest`. Wybierz **OK**.

     BankLoadTest web wydajności i obciążenia projektu testowego jest dodawany do rozwiązania.

4. Otwórz menu skrótów dla nowej wydajności sieci web bankloadtest i Załaduj projekt testowy, wybierz opcję **Dodaj**, a następnie wybierz **Test obciążenia**.

5. **Nowego kreatora testu obciążenia** rozpoczyna się.

6. **Powitalnej** strony **nowego kreatora testu obciążenia** to pierwsza strona.

7. Wybierz **dalej**.

### <a name="to-edit-settings-for-load-test-scenario"></a>Aby edytować ustawienia scenariusza testu obciążenia

1. W **wprowadź nazwę scenariusza testu obciążeniowego** polu tekstowym **ScenarioSample**.

     A *scenariusza* jest mechanizmem grupowania. Składa się z zestawu testów oraz właściwości do uruchamiania tych testów pod obciążeniem.

2. Ustaw **czas namysłu profilu** do `Use normal distribution centered on recorded think times`. Czasy reakcji reprezentują czas, jaki użytkownik może spędzać na stronie sieci web przed przejściem do następnej strony.

1. Wybierz **dalej** po zakończeniu.

### <a name="to-edit-load-pattern-setting-for-test-scenario"></a>Aby edytować ustawienia ścieżki obciążenia scenariuszu testu

1. Wybierz **obciążenia krokowego**.

    > [!NOTE]
    > Można wybrać spośród dwóch rodzajów wzorców obciążenia: stałego i krokowego. Każdy typ ma swoją funkcję w testowaniu obciążenia, ale dla celów tego instruktażu wybierz **obciążenia krokowego**.

2. Ustaw **zacznij liczyć użytkowników** do 10 użytkowników.

3. Ustaw **czas trwania kroku** to 10 sekund.

4. Ustaw **liczba użytkowników zwiększana podczas kroku** do 10 użytkowników/krok.

5. Ustaw **maksymalna liczba użytkowników** do 100 użytkowników.

6. Wybierz **dalej**.

### <a name="to-select-test-mix-model-for-the-scenario"></a>Aby wybrać model mieszaniny testu dla scenariusza

1. W obszarze **jak powinny być modelowane mieszaniny testów**, wybierz opcję **na podstawie całkowitej liczby testów**.

2. Wybierz **dalej**.

### <a name="to-add-unit-tests-to-the-scenario"></a>Aby dodać testy jednostek do scenariusza

1. Następnym krokiem jest **Dodaj testy do obciążenia scenariusza testu i Edytuj test mieszany**.

2. Wybierz **Dodaj** aby wybrać testy.

3. Wybierz **CreditTest** testów jednostkowych, na liście **dostępne testy** okienko, które wyświetla listę wszystkich testów wydajności sieci web i testów jednostkowych w projekt testu obciążenia i wydajności sieci web.

4. Wybierz strzałkę, aby dodać **CreditTest** testu jednostkowego do testowania **wybrane testy** okienka.

5. Powtórz kroki 3 i 4 dla **DebitTest** i **FreezeAccountTest** testów jednostkowych.

6. Po zakończeniu dodawania trzech jednostek testowych wybierz **OK**.

     Zostanie wyświetlona testu mieszanego.

7. Przesuń suwak w obszarze **dystrybucji** dla **CreditTest** nieznacznie się po prawej stronie, aby dopasować rozkład testu. Należy zauważyć, że inne suwaki przesuwają się po lewej stronie automatycznie tak, że rozkład pozostaje na poziomie 100%.

8. Wybierz **dalej**.

### <a name="to-select-network-mix-for-test-scenario"></a>Aby wybrać mieszaninę sieci dla scenariusza testu

1. Wybierz typ połączenia sieci LAN, aby dodać do mieszanki przepustowości sieci.

     Możesz dodać więcej typów sieci. Użyj suwaków, aby dopasować test dystrybucji i wagi.

2. Wybierz **dalej**.

### <a name="to-specify-computers-to-monitor-with-counter-sets-during-load-test-run"></a>Aby określić komputery, aby monitorować zbiorem liczników podczas przebiegu testu obciążeniowego

1. Wybierz **dalej**.

     Aby uzyskać więcej informacji na temat zbiory liczników, zobacz [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążeniowym](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

### <a name="to-edit-run-setting-for-load-test"></a>Aby edytować ustawienia przebiegu testu obciążeniowego

1. Wybierz **czas trwania testu obciążenia** , a następnie ustaw **czas trwania uruchomienia** jako 2 minuty w celu *testu dymu* testu obciążenia.

     W przypadku tworzenia testów obciążenia, jest dobrym rozwiązaniem, aby sprawdzić, czy wszystko jest poprawnie skonfigurowane i działa zgodnie z oczekiwaniami, uruchamiając krótki, lekki test obciążenia. Ten proces jest nazywany *test działania*.

2. Wybierz **Zakończ**. Test obciążenia jest otwierany w **edytorze testu obciążenia**.

## <a name="run-the-load-test"></a>Uruchom test obciążenia
 Po utworzeniu testu obciążenia uruchom go, aby obejrzeć, jak aplikacja bankowa zareaguje na symulację obciążenia. Gdy uruchomiony jest test obciążenia, zobacz **analizatora testu obciążenia** okna.

### <a name="to-run-the-load-test"></a>Aby uruchomić test obciążenia

1. Otwórz w programie testu obciążenia **edytorze testu obciążenia**, wybierz zielony **Uruchom Test** przycisku na pasku narzędzi. Test obciążenia rozpoczyna się.

2. Jeśli Symulacja testu przekracza jakiekolwiek progi, ikony pojawiają się w węzłach drzewa w celu wskazania przekroczenia progu. Błędy mają czerwone kółko nakładki, a ostrzeżenia mają żółty trójkąt nakładki. Możesz znaleźć licznik, który przekroczył próg i jej wykres, przeciągając jego ikonę na wykres. Można to zrobić, gdy uruchomiony jest test.

## <a name="see-also"></a>Zobacz także

- [Edytuj test mieszany, aby określić, które testy, aby uwzględnić w scenariuszu testu obciążenia](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Określanie typów sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md)
- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Edytowanie wzorców obciążenia w celu modelu aktywności wirtualnych użytkowników](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Edytowanie modeli testów mieszanych w celu określania prawdopodobieństwa użytkownik wirtualny uruchomi testu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)