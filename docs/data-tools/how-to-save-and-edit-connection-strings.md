---
title: 'Porady: zapisywanie i edycja parametrów połączeń'
description: Dowiedz się, jak zapisywać i edytować parametry połączenia w aplikacjach Visual Studio. Zapisz lub Edytuj parametry połączenia bezpośrednio w ustawieniach aplikacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 1707bbdd458ba6fc57ea3f6897af40e4cb9b4f03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866739"
---
# <a name="how-to-save-and-edit-connection-strings"></a>Instrukcje: zapisywanie i edytowanie parametrów połączenia
Parametry połączenia w aplikacjach Visual Studio są zapisywane w pliku konfiguracyjnym aplikacji (nazywanego również ustawieniami aplikacji) lub trwale kodowane bezpośrednio w aplikacji. Zapisywanie parametrów połączenia w pliku konfiguracji aplikacji upraszcza zadanie obsługi aplikacji. Jeśli parametry połączenia należy zmienić, można je zaktualizować w pliku ustawień aplikacji (w przeciwieństwie do zmiany w kodzie źródłowym i ponownej kompilacji aplikacji).

Przechowywanie poufnych informacji (takich jak hasło) w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji. Parametry połączenia zapisane w pliku konfiguracyjnym aplikacji nie są szyfrowane ani zasłaniane, dlatego może być możliwe, aby ktoś mógł uzyskać dostęp do pliku i wyświetlić jego zawartość. Używanie zintegrowanych zabezpieczeń systemu Windows jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych.

Jeśli nie zdecydujesz się używać zintegrowanych zabezpieczeń systemu Windows, a Twoja baza danych wymaga nazwy użytkownika i hasła, możesz pominąć je w parametrach połączenia, ale aplikacja będzie musiała podać te informacje, aby pomyślnie połączyć się z bazą danych. Na przykład można utworzyć okno dialogowe, które będzie monitował użytkownika o te informacje, i dynamicznie kompiluje parametry połączenia w czasie wykonywania. W przypadku przechwycenia informacji na drodze do bazy danych może być nadal przyczyną problemu.
Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Aby zapisać parametry połączenia z poziomu kreatora konfiguracji źródła danych
W **Kreatorze konfiguracji źródła danych** wybierz opcję zapisu połączenia na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** .

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Aby zapisać parametry połączenia bezpośrednio w ustawieniach aplikacji
1. W **Eksplorator rozwiązań** kliknij dwukrotnie ikonę **mój projekt** (Visual Basic) lub ikonę **Właściwości** (C#), aby otworzyć **projektanta projektu**.
1. Wybierz kartę **Ustawienia**.
1. Wprowadź **nazwę** parametrów połączenia. Odnosi się do tej nazwy podczas uzyskiwania dostępu do parametrów połączenia w kodzie.
1. Ustaw **Typ** na (**Parametry połączenia**).
1. Pozostaw **zakres** ustawiony na wartość **aplikacja**.
1. Wpisz parametry połączenia w polu **wartość** lub kliknij przycisk **wielokropka** (...) w polu **wartość** , aby otworzyć okno dialogowe **Właściwości połączenia** w celu skompilowania parametrów połączenia.

## <a name="edit-connection-strings-stored-in-application-settings"></a>Edytuj parametry połączenia przechowywane w ustawieniach aplikacji
Informacje o połączeniu zapisane w ustawieniach aplikacji można zmodyfikować przy użyciu **projektanta projektu**.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Aby edytować parametry połączenia przechowywane w ustawieniach aplikacji
1. W **Eksplorator rozwiązań** kliknij dwukrotnie ikonę **mój projekt** (Visual Basic) lub ikonę **Właściwości** (C#), aby otworzyć **projektanta projektu**.
1. Wybierz kartę **Ustawienia**.
1. Znajdź połączenie, które chcesz edytować, a następnie wybierz tekst w polu **wartość** .
1. Edytuj parametry połączenia w polu **wartość** lub kliknij przycisk **wielokropka** (...) w polu **wartość** , aby edytować połączenie przy użyciu okna dialogowego **Właściwości połączenia** .

## <a name="edit-connection-strings-for-datasets"></a>Edytuj parametry połączenia dla zestawów danych
Informacje o połączeniu dla każdego TableAdapteru można zmodyfikować w zestawie danych.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Aby edytować parametry połączenia dla elementu TableAdapter w zestawie danych
1. W **Eksplorator rozwiązań** kliknij dwukrotnie zestaw danych (plik **XSD** ), który ma połączenie, które chcesz edytować.
1. Wybierz **TableAdapter** lub zapytanie z połączeniem, które chcesz edytować.
1. W oknie **Właściwości** rozwiń **węzeł połączenie**.
1. Aby szybko zmodyfikować parametry połączenia, Edytuj Właściwość **ConnectionString** lub kliknij strzałkę w dół we właściwości **połączenie** i wybierz pozycję **nowe połączenie**.

## <a name="security"></a>Zabezpieczenia
Przechowywanie poufnych informacji (takich jak hasło) w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji. Używanie zintegrowanych zabezpieczeń systemu Windows jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych.
Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="see-also"></a>Zobacz też

- [Dodawanie połączeń](../data-tools/add-new-connections.md)
