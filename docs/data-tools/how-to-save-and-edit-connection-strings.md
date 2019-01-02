---
title: 'Instrukcje: Zapisywanie i Edycja parametrów połączeń'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 96c55b44e6e6ebbfba27c4daf10512cefe1fd393
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53961273"
---
# <a name="how-to-save-and-edit-connection-strings"></a>Instrukcje: Zapisywanie i edytowanie parametrów połączeń
Parametry połączenia w aplikacjach Visual Studio są zapisywane w pliku konfiguracyjnym aplikacji (nazywane także ustawienia aplikacji) lub zakodowane bezpośrednio w aplikacji. Zapisywanie ciągów połączenia w pliku konfiguracji aplikacji upraszcza zadanie obsługi aplikacji. Jeśli parametry połączenia muszą być zmienione, należy je zaktualizować w pliku ustawień aplikacji (w przeciwieństwie do konieczności odbywają się w kodzie źródłowym i ponownie skompilować aplikację).

Przechowywanie poufnych informacji (na przykład hasło) w ciągu połączenia mogą wpływać na bezpieczeństwo aplikacji. Parametry połączenia, zapisane w pliku konfiguracji aplikacji nie są szyfrowane lub zaciemniony w plikach, dlatego może być osoba uzyskać dostęp do pliku i wyświetlić jego zawartość. Korzysta ze zintegrowanych zabezpieczeń Windows jest Bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych.

Jeśli użytkownik nie chce używać Windows zintegrowane zabezpieczenia baza danych wymaga nazwy użytkownika i hasła, można je pominąć w ciągu połączenia, a aplikacja będzie konieczne udostępnienie tych informacji do pomyślnego połączenia z bazą danych. Na przykład można utworzyć okno dialogowe, który monituje użytkownika o te informacje i dynamicznie tworzy ciąg połączenia w czasie wykonywania. Zabezpieczenia nadal może być problemem, jeśli informacje zostaną przechwycone w drodze do bazy danych.
Aby uzyskać więcej informacji, zobacz [ochrona informacji o połączeniu](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Aby zapisać parametry połączenia z w ramach Kreatora konfiguracji źródła danych
W **Kreatora konfiguracji źródła danych**, wybierz opcję, aby zapisać połączenie na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** strony.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Aby zapisać parametry połączenia bezpośrednio w aplikacji ustawienia
1. W **Eksploratora rozwiązań**, kliknij dwukrotnie **mój projekt** ikonę (Visual Basic) lub **właściwości** ikonę (C#) aby otworzyć **projektanta projektu**.
1. Wybierz **ustawienia** kartę.
1. Wprowadź **nazwa** ciągu połączenia. Podczas uzyskiwania dostępu do ciągu połączenia w kodzie należy odwoływać się do tej nazwy.
1. Ustaw **typu** do (**parametry połączenia**).
1. Pozostaw **zakres** równa **aplikacji**.
1. Wpisz parametry połączenia do **wartość** pola, lub kliknij przycisk **wielokropka** przycisku (...) w **wartość** pole, aby otworzyć **właściwości połączenia** okno dialogowe Tworzenie parametrów połączenia.

## <a name="edit-connection-strings-stored-in-application-settings"></a>Edytuj parametry połączenia przechowywana w ustawieniach aplikacji
Możesz zmodyfikować informacje o połączeniu, który został zapisany w ustawieniach aplikacji przy użyciu **projektanta projektu**.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Aby edytować ciąg połączenia przechowywana w ustawieniach aplikacji
1. W **Eksploratora rozwiązań**, kliknij dwukrotnie **mój projekt** ikonę (Visual Basic) lub **właściwości** ikonę (C#) aby otworzyć **projektanta projektu**.
1. Wybierz **ustawienia** kartę.
1. Znajdź połączenie, o których chcesz edytować, a następnie zaznacz tekst w **wartość** pola.
1. Edytuj parametry połączenia w **wartość** pola, lub kliknij przycisk **wielokropka** przycisku (...) w **wartość** pole, aby edytować połączenie za pomocą **połączenia Właściwości** okno dialogowe.

## <a name="edit-connection-strings-for-datasets"></a>Edytuj parametry połączenia dla zestawów danych
Można zmodyfikować informacje o połączeniu dla każdy obiekt TableAdapter w zestawie danych.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Aby edytować parametry połączenia dla TableAdapter w zestawie danych
1. W **Eksploratora rozwiązań**, kliknij dwukrotnie zestaw danych (**XSD** pliku) zawierający połączenia, którą chcesz edytować.
1. Wybierz **TableAdapter** lub kwerendę, która ma połączenie, którą chcesz edytować.
1. W **właściwości** okna, rozwiń węzeł **węzła połączenia**.
1. Aby szybko zmodyfikować parametry połączenia, należy edytować **ConnectionString** właściwości, lub kliknij strzałkę w dół na **połączenia** właściwości i wybierz polecenie **nowe połączenie**.

## <a name="security"></a>Zabezpieczenia
Przechowywanie poufnych informacji (na przykład hasło) w ciągu połączenia mogą wpływać na bezpieczeństwo aplikacji. Korzysta ze zintegrowanych zabezpieczeń Windows jest Bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych.
Aby uzyskać więcej informacji, zobacz [ochrona informacji o połączeniu](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="see-also"></a>Zobacz także

- [Dodawanie połączeń](../data-tools/add-new-connections.md)