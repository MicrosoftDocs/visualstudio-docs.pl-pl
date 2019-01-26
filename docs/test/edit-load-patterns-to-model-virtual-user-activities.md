---
title: Wzorce obciążenia dla testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
- load tests, scenarios
- load tests, virtual users
ms.assetid: 0ba0363b-7f50-4bde-a919-0e3bce7bc115
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: 4f8e80fa9568bf418b972a3e2dd77d9141ba829f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932730"
---
# <a name="edit-load-patterns-to-model-virtual-user-activities"></a>Edytowanie wzorców obciążenia w celu modelu aktywności wirtualnych użytkowników

Właściwości szablonu obciążenia określają o tym, jak symulowane obciążenie użytkownika jest korygowane w trakcie testu obciążenia. Program Visual Studio zapewnia trzy wbudowane wzorce ładowania: stałe, etapu i ukierunkowane na cel. Możesz wybrać wzorzec obciążenia i dostosować właściwości do odpowiednich poziomów dla swoich celów testu obciążenia.

Wzorzec obciążenia jest składnikiem scenariusza. Scenariusze, wraz z ich wzorców obciążenia zdefiniowanych obejmują test obciążenia.

> [!NOTE]
> We wzorcach obciążenia wszystkie obciążenia, który generuje programie Visual Studio jest symulowane obciążenia użytkowników wirtualnych.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-patterns"></a>Wzorce obciążenia

### <a name="constant"></a>Stała

 Wzór obciążenia stałej jest używany do określenia obciążenia użytkownikami, która nie zmienia się podczas testu obciążeniowego. Na przykład po uruchomieniu testu dymu w aplikacji sieci web, warto ustawić światła, stała obciążenia 10 użytkowników.

#### <a name="constant-load-pattern-considerations"></a>Zagadnienia dotyczące wzoru stałego obciążenia

 Wzór obciążenia stałej jest używany do uruchamiania tego samego obciążenia użytkownika podczas uruchamiania testu obciążenia. Zachować ostrożność przy używaniu wzoru stałego obciążenia, który ma dużą liczbą użytkowników; Spowoduje to więc umieścić nieuzasadnione i nierealistyczne żądania na serwerze lub serwerach, na początku testu obciążenia. Na przykład jeśli test obciążenia zawiera test sieci web, który rozpoczyna się żądaniem do strony głównej i ustawisz test obciążenia przy stałym obciążeniu 1000 użytkowników, test obciążeniowy, prześle pierwsze 1000 żądań do strony głównej tak szybko, jak to możliwe. To może nie być realistyczna symulacja rzeczywistego dostępu do witryny sieci Web. Aby rozwiązać ten problem, należy wziąć pod uwagę przy użyciu krokowego wzorca obciążenia, który stopniowo zwiększa się do 1000 użytkowników jednocześnie lub określić okres rozgrzewania w ustawieniach testu obciążenia. Jeśli określono okres rozgrzewania, test obciążeniowy automatycznie zwiększy obciążenie stopniowo w okresie rozgrzewania. Aby uzyskać więcej informacji, zobacz [Konfigurowanie opóźnień uruchamiania scenariuszy](../test/configure-scenario-start-delays.md).

### <a name="step"></a>Krok

 Krokowego wzorca obciążenia służy do określania obciążenie użytkownikami, która zwiększa z czasem do zdefiniowanych maksymalne obciążenie użytkownikami. Dla obciążeń przechodzenie krok po kroku, należy określić **początkowa liczba użytkowników**, **maksymalna liczba użytkowników**, **czas trwania kroku (w sekundach)**, i **liczba użytkowników zwiększana podczas kroku**.

 Na przykład obciążenia krokowego z **początkowa liczba użytkowników** jednego, **maksymalna liczba użytkowników** 100, **czas trwania kroku (w sekundach)** 10, a **liczbę użytkowników** 1 tworzy wzorzec obciążenia użytkownika, który rozpoczyna się od 1, zwiększa się o 1 co 10 sekund, aż do osiągnięcia 100 użytkowników.

> [!NOTE]
> Jeśli czas trwania całkowita testu jest krótszy niż czas, który jest wymagany do kroku maksymalnie maksymalne obciążenie użytkownikami, a następnie zatrzyma się po czas trwania testu, a nie dociera **maksymalna liczba użytkowników** docelowej.


 Celem kroku umożliwia zwiększenie obciążenia, dopóki serwer osiągnie punkt którym wydajności znacznie zmniejsza. W miarę wzrostu obciążenia serwera po pewnym czasie wyczerpania zasobów. Obciążenia krokowego to dobry sposób, aby określić liczbę użytkowników, w których ten problem wystąpi. Korzystając z obciążenia przechodzenia krok po kroku masz również monitorowanie zasobów agenta ściśle, aby upewnić się, że agenci mogą wygenerowania pożądanego obciążenia.

 Zazwyczaj należy przeprowadzić kilku uruchomień, które mają czas trwania kroku innego użytkownika krok liczby i tak, że można uzyskać dobrą miary dla danego obciążenia. Często obciążeń Pokaż początkowej kolekcji, dla każdego kroku, jak użytkownicy są dodawani. Zawierający obciążenia po tym kursie służy do mierzenia wydajności systemu, po odzyskiwania systemu od początkowego kolekcji.

#### <a name="step-load-pattern-considerations"></a>Zagadnienia dotyczące wzorca obciążenia krok

 Krokowego wzorca obciążenia może służyć do uruchomienia testów obciążenia, dzięki czemu można zobaczyć, jak wydajność zmienia się wraz ze wzrostem obciążenia użytkownika to zwiększenie obciążenia na serwerze lub serwerach. Na przykład, aby zobaczyć, jak wykonać serwer lub serwery jako obciążenie użytkownikami wzrasta do 2000 użytkowników, może uruchomić 10-godzinny test obciążenia przy użyciu krokowego wzorca obciążenia, który ma następujące właściwości:

- **Początkowa liczba użytkowników**: 100

- **Maksymalna liczba użytkowników**: 2000

- **Czas trwania kroku (w sekundach)**: 1,800

- **Czas narastania (w sekundach)**: 20

- **Liczba użytkowników zwiększana podczas kroku**: 100

  Te ustawienia, uruchom test obciążenia w ciągu 30 minut (1800 sekund) po użytkownik ładuje 100, 200, 300, a także do 2000 użytkowników. **Czas do zwiększenia kroku** właściwość warto szczególnej uwagi, ponieważ jest tylko jeden z tych właściwości, która nie jest dostępna do wyboru w **nowego kreatora testu obciążenia**. Ta właściwość umożliwia zwiększenie od jednego kroku do następnego (na przykład od 100 do 200 użytkowników), nastąpi stopniowo, a nie od razu. W przykładzie obciążenia użytkownikami zwiększyłoby się ze 100 do 200 użytkowników w okresie 20 sekund (wzrost o 5 użytkowników co sekundę). Aby uzyskać więcej informacji, zobacz [jak: Określanie właściwości czasu narastania kroku dla wzorca obciążenia krokowego](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md).

### <a name="goal-based"></a>Opartego na celach

 Wzorca obciążenia opartego na celach przypomina krokowego wzorca, ale dopasowuje obciążenie użytkownikami, na podstawie progów licznika wydajności i dopasowania obciążenia okresowe użytkownika. Obciążenia opartego na celach są przydatne w wielu różnych celów:

- Maksymalizacja dane wyjściowe z agentów: pomiar klucz ograniczanie metryki na agencie w celu zmaksymalizowania dane wyjściowe agentów. Typowo jest Procesora; Jednak może również być pamięci.

- Osiągnie pewien poziom zasobów docelowych, zwykle procesora CPU, na serwerze docelowym, następnie pomiaru przepływności na tym samym poziomie. Dzięki temu można wykonać porównania w celu uruchamiania przepływności, biorąc pod uwagę spójne poziom użycia zasobów na serwerze.

- Docieranie do docelowego poziomu przepływności, na serwerze.

  W poniższej tabeli przedstawiono przykład pokazuje opartego na celach wzorzec z następującymi ustawieniami właściwości:

|Grupa właściwości|Właściwość|Wartość|
|-|--------------|-|
|Licznik wydajności|Kategoria|Procesor|
|Licznik wydajności|Komputer|ContosoServer1|
|Licznik wydajności|Licznik|Czas procesora (%)|
|Licznik wydajności|Wystąpienie|_Total|
|Zakres docelowy dla licznika wydajności|Wysokiej klasy|90|
|Zakres docelowy dla licznika wydajności|Niskiej klasy|70|
|Limity liczby użytkowników|Początkowa liczba użytkowników|1|
|Limity liczby użytkowników|Maksymalna liczba użytkowników|100|
|Limity liczby użytkowników|Maksymalne zmniejszenie liczby użytkowników|5|
|Limity liczby użytkowników|Maksymalne zwiększenie liczby użytkowników|5|
|Limity liczby użytkowników|Minimalna liczba użytkowników|1|

 Te ustawienia powodują **analizatora testu obciążenia** dostosowania obciążenie użytkownikami, od 1 do 100 podczas testu w taki sposób, który **licznika** dla `% Processor Time` z ruchów WebServer01 między `70%`i `90%.`

 Rozmiar każdego dopasowania obciążenie użytkownika jest określany przez **maksymalne zwiększenie liczby użytkowników** i **maksymalne zmniejszenie liczby użytkowników** ustawienia. Limity liczby użytkowników są ustalane przez **maksymalna liczba użytkowników** i **minimalna liczba użytkowników** właściwości.

#### <a name="goal-based-load-pattern-considerations"></a>Zagadnienia dotyczące wzorca obciążenia opartego na celach

 Wzorca obciążenia opartego na celach jest przydatne, jeśli chcesz określić liczbę użytkowników, których system może obsłużyć, zanim osiągnie pewien poziom wykorzystania zasobów. Ta opcja działa najlepiej, gdy już zidentyfikowano zasobem ograniczającym (czyli wąskie gardło) w systemie.

 Na przykład załóżmy, że wiesz, że zasobem ograniczającym w systemie jest Procesor na serwerze bazy danych i chcesz zobaczyć, ilu użytkowników mogą być obsługiwane, gdy Procesor na serwerze bazy danych jest zajęty około 75 procent. Można użyć wzorca obciążenia opartego na celach mającego celu utrzymania wartość wydajności licznika "% czasu procesora" między 70 procent i 80 procent.

 Jedną z rzeczy Zwróć uwagę na to, jeśli niektóre inny zasób ogranicza przepustowość systemu. Takich zasobów może powodować cel, który jest określony przez wzorzec obciążenia opartego na celach, nigdy nie zostanie osiągnięta. Ponadto obciążenia użytkownikami będą nadal wzrasta do czasu wartość, która jest określona dla **maksymalna liczba użytkowników** zostanie osiągnięty. Zazwyczaj nie jest to pożądane obciążenie, więc należy ostrożność podczas wyboru licznika wydajności we wzorcu obciążenia opartego na celach.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Określanie wzorzec ładowania początkowego dla testu obciążeniowego:** Po utworzeniu testu obciążenia przy użyciu **Kreatora nowego testu obciążeniowego**, wybierz wzorzec obciążenia.|-   [Zmień wzorzec obciążenia](../test/edit-load-patterns-to-model-virtual-user-activities.md#change-the-load-pattern)|
|**Edytowanie wzorzec obciążenia dla testu obciążeniowego:** Po utworzeniu testu obciążenia, można edytować wzorca obciążenia w **edytora testu obciążenia**.|-   [Jak: Określanie właściwości czasu narastania kroku dla wzorca obciążenia krokowego](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|
|**Określanie, czy użytkownicy wirtualni w obciążenia scenariusza testu powinien zawierać dane pamięci podręcznej sieci web:** Możesz zmienić **procent nowych użytkowników** właściwości wpływają na sposób, w którym zasymulowano obciążenie pamięci podręcznej sieci web będą wykonywane przez przeglądarkę sieci web dla użytkowników wirtualnych.|-   [Jak: Określ wartość procentową użytkowników wirtualnych korzystających z danych w pamięci podręcznej sieci web](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)|
|**Określanie czas do zwiększenia kroku dla wzorca obciążenia krokowego:** **Czas do zwiększenia kroku** właściwość umożliwia zwiększenie od jednego kroku do następnego (na przykład od 100 do 200 użytkowników), nastąpi stopniowo, a nie od razu.|-   [Jak: Określanie właściwości czasu narastania kroku dla wzorca obciążenia krokowego](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|

## <a name="change-the-load-pattern"></a>Zmień wzorzec obciążenia

 Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążeniowego**, możesz użyć **edytora testu obciążenia** można zmienić właściwości szablonu obciążenia, które są skojarzone ze scenariuszem do poziomu, który spełnia Twoje cele testu.

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testów obciążenia wraz z opisami, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).


 Wzorzec obciążenia określa liczbę użytkowników wirtualnych aktywnych podczas testu obciążenia i szybkość jaką nowi użytkownicy są dodawani. Możesz wybrać spośród trzech dostępnych wzorców: krok wzorca, stała i opartego na celach. Aby uzyskać więcej informacji, zobacz [Określ liczbę użytkowników wirtualnych przy użyciu wzorców obciążenia w scenariuszu testu obciążenia](../test/edit-load-patterns-to-model-virtual-user-activities.md).

> [!NOTE]
> Możesz również zmienić właściwości obciążenia programowo przy użyciu wtyczki testu obciążeniowego. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie wtyczki testu obciążeniowego](../test/how-to-create-a-load-test-plug-in.md).


### <a name="to-change-the-load-pattern"></a>Aby zmienić wzorzec obciążenia

1.  Otwórz test obciążenia.

2.  W **edytorze testu obciążeniowego**w *scenariuszy* folder, rozwiń węzeł scenariusz, aby edytować wzorzec obciążenia i wybrać wzorzec obciążenia dla scenariusza.

    > [!NOTE]
    > Treść węzła wzorca obciążenia, jest wyświetlany w drzewie scenariusza w teście obciążenia odzwierciedla profilu obciążenia, można wybrać podczas tworzenia obciążenia testu. Może być albo **stałej Załaduj profil** lub **kroku Załaduj profil**.

3.  Naciśnij klawisz **F4** do wyświetlenia **właściwości** okna.

     **Wzorca obciążenia** i **parametry** kategorii są wyświetlane w **właściwości** okna.

4.  (Opcjonalnie) Zmiana **wzorzec** właściwość **wzorca obciążenia** kategorii.

     Wybrane opcje dla **wzorzec** właściwości są **kroku**, **stałej**, i **na podstawie celem**. Aby uzyskać więcej informacji na temat typów wzorca obciążenia, zobacz [Określ liczbę użytkowników wirtualnych przy użyciu wzorców obciążenia w scenariuszu testu obciążenia](../test/edit-load-patterns-to-model-virtual-user-activities.md).

5.  (Opcjonalnie) W **parametry** kategorii, zmień wartości.

    > [!NOTE]
    > Wartości można ustawić dla **parametry** różnią się w zależności od wartości, które zostały wybrane do **wzorzec** właściwości.

6.  Po zmianie właściwości, wybierz **Zapisz** na **pliku** menu. Następnie można uruchomić test obciążenia przy użyciu nowego wzorca obciążenia.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Instrukcje: Określ wartość procentową użytkowników wirtualnych korzystających z danych w pamięci podręcznej sieci web](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)
- [Instrukcje: Określanie właściwości czasu narastania kroku dla wzorca obciążenia krokowego](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)