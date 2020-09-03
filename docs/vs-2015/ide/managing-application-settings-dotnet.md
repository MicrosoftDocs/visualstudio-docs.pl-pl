---
title: Zarządzanie ustawieniami aplikacji (.NET) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
ms.assetid: 35254321-ad14-47d9-b8c6-39ab3203c5d9
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85cc90170b2dc665bcdd5acd97860c47ef5a14c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74293871"
---
# <a name="managing-application-settings-net"></a>Zarządzanie ustawieniami aplikacji (.NET)

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ustawienia aplikacji umożliwiają dynamiczne przechowywanie informacji o aplikacji. Ustawienia umożliwiają przechowywanie na komputerze klienckim informacji, które nie powinny być dołączone do kodu aplikacji (na przykład parametrów połączenia), preferencji użytkownika i innych informacji potrzebnych w czasie wykonywania.

Ustawienia aplikacji zastępują właściwości dynamiczne używane we wcześniejszych wersjach programu Visual Studio.

Każde ustawienie aplikacji musi mieć unikatową nazwę. Nazwa może być dowolną kombinacją liter, cyfr lub znaku podkreślenia, który nie zaczyna się od cyfry i nie może zawierać spacji. Nazwę można zmienić za pomocą `Name` właściwości.

Ustawienia aplikacji mogą być przechowywane jako dowolny typ danych, który może być serializowany do kodu XML lub ma `TypeConverter` zaimplementowany `ToString` / `FromString` . Najczęściej używane typy to `String` , `Integer` , i `Boolean` , ale można również przechowywać wartości jako <xref:System.Drawing.Color> <xref:System.Object> Parametry połączenia.

Ustawienia aplikacji zawierają również wartość. Wartość jest ustawiana za pomocą właściwości **Value** i musi być zgodna z typem danych ustawienia.

Ponadto ustawienia aplikacji mogą być powiązane z właściwością formularza lub kontrolki w czasie projektowania.

Istnieją dwa typy ustawień aplikacji na podstawie zakresu:

- Ustawienia zakresu aplikacji mogą służyć jako informacje takie jak adres URL dla usługi sieci Web lub parametry połączenia z bazą danych. Te wartości są skojarzone z aplikacją. W związku z tym użytkownicy nie mogą zmienić ich w czasie wykonywania.

- Ustawienia o zakresie użytkownika mogą służyć do takich informacji, jak utrwalanie ostatniej pozycji formularza lub preferencji czcionki. Użytkownicy mogą zmieniać te wartości w czasie wykonywania.

  Typ ustawienia można zmienić za pomocą właściwości **SCOPE** .

  System projektu przechowuje ustawienia aplikacji w dwóch plikach XML: plik app.config, który jest tworzony w czasie projektowania podczas tworzenia pierwszego ustawienia aplikacji; i plik user.config, który jest tworzony w czasie wykonywania, gdy użytkownik, który uruchamia aplikację, zmienia wartość dowolnego ustawienia użytkownika. Zwróć uwagę, że zmiany ustawień użytkownika nie są zapisywane na dysku, chyba że aplikacja wywołuje metodę, aby to zrobić.

## <a name="creating-application-settings-at-design-time"></a>Tworzenie ustawień aplikacji w czasie projektowania

W czasie projektowania można utworzyć ustawienia aplikacji na dwa sposoby: za pomocą strony **Ustawienia** **projektanta projektu**lub za pomocą okna **Właściwości** formularza lub kontrolki, co pozwala powiązać ustawienie z właściwością.

W przypadku tworzenia ustawienia o zakresie aplikacji (na przykład parametrów połączenia z bazą danych lub odwołania do zasobów serwera) program [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zapisuje je w app.config przy użyciu `<applicationSettings>` znacznika. (Parametry połączenia są zapisywane pod `<connectionStrings>` tagiem).

Podczas tworzenia ustawienia o zakresie użytkownika (na przykład czcionki domyślnej, strony głównej lub rozmiaru okna), program [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zapisuje ją w app.config przy użyciu `<userSettings>` znacznika.

> [!IMPORTANT]
> W przypadku przechowywania parametrów połączenia w app.config należy podjąć odpowiednie środki ostrożności, aby uniknąć ujawnienia poufnych informacji, takich jak hasła lub ścieżki serwera, w parametrach połączenia.
>
> W przypadku korzystania z informacji o parametrach połączenia z zewnętrznego źródła, takiego jak podanie identyfikatora użytkownika i hasła, należy zachować ostrożność, aby upewnić się, że wartości używane do konstruowania parametrów połączenia nie zawierają dodatkowych parametrów połączenia, które zmieniają zachowanie połączenia.
>
> Rozważ użycie funkcji konfiguracja chroniona do szyfrowania poufnych informacji w pliku konfiguracji. Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](https://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4) .

> [!NOTE]
> Ponieważ nie istnieje model plików konfiguracji dla bibliotek klas, ustawienia aplikacji nie są stosowane dla projektów biblioteki klas. Wyjątkiem jest Visual Studio Tools projektu DLL pakietu Office, który może mieć plik konfiguracji.

## <a name="using-customized-settings-files"></a>Używanie niestandardowych plików ustawień

Możesz dodać dostosowane pliki ustawień do projektu, aby wygodnie zarządzać grupami ustawień. Ustawienia, które są zawarte w pojedynczym pliku, są ładowane i zapisywane jako jednostka. W związku z tym, możliwość przechowywania ustawień w osobnych plikach dla często używanych i rzadko używanych grup może zaoszczędzić czas podczas ładowania i zapisywania ustawień.

Na przykład można dodać do projektu plik, taki jak SpecialSettings. Settings. Gdy `SpecialSettings` Klasa nie jest ujawniona w `My` przestrzeni nazw, **Wyświetl kod** może odczytać plik ustawień niestandardowych, który zawiera `Partial Class SpecialSettings` .

Projektant ustawień najpierw szuka pliku Settings. Settings tworzonego przez system projektu; jest to domyślny plik wyświetlany przez projektanta projektu na karcie **Ustawienia** . Settings. Settings znajduje się w folderze my Project dla [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projektów i w folderze właściwości dla [!INCLUDE[csprcs](../includes/csprcs-md.md)] projektów. Projektant projektu następnie wyszukuje inne pliki ustawień w folderze głównym projektu. W związku z tym należy umieścić w tym miejscu plik ustawień niestandardowych. Jeśli dodasz plik. Settings w innym miejscu projektu, Projektant projektu nie będzie mógł go zlokalizować.

## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-basic"></a>Uzyskiwanie dostępu do lub zmiana ustawień aplikacji w czasie wykonywania w Visual Basic

W [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projektach można uzyskać dostęp do ustawień aplikacji w czasie wykonywania przy użyciu `My.Settings` obiektu. Na stronie **Ustawienia** kliknij przycisk **Wyświetl kod** , aby wyświetlić plik Settings. vb. Settings. vb definiuje `Settings` klasę, która umożliwia obsługę tych zdarzeń w klasie Settings: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> , <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged> , <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded> i <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> . Należy zauważyć, że `Settings` Klasa w Settings. vb jest klasą częściową, która wyświetla tylko kod należący do użytkownika, a nie całą wygenerowaną klasę. Aby uzyskać więcej informacji na temat uzyskiwania dostępu do ustawień aplikacji za pomocą `My.Settings` obiektu, zobacz [dostęp do ustawień aplikacji](https://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e).

Wartości wszelkich ustawień o zakresie użytkownika, które użytkownik zmienia w czasie wykonywania (na przykład pozycja formularza), są przechowywane w pliku user.config. Zwróć uwagę, że wartości domyślne są nadal zapisywane w app.config.

Jeśli wszystkie ustawienia o zakresie użytkownika zostały zmienione w czasie wykonywania, na przykład w testowaniu aplikacji i chcesz zresetować te ustawienia do wartości domyślnych, kliknij przycisk **Synchronizuj** .

Zdecydowanie zalecamy użycie `My.Settings` obiektu i domyślnego pliku. Settings w celu uzyskania dostępu do ustawień. Jest to spowodowane tym, że można użyć projektanta ustawień do przypisywania właściwości do ustawień, a ponadto ustawienia użytkownika zostaną automatycznie zapisane przed zamknięciem aplikacji. Jednak [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] aplikacja może uzyskiwać dostęp do ustawień bezpośrednio. W takim przypadku musisz uzyskać dostęp do `MySettings` klasy i użyć pliku Custom. Settings w katalogu głównym projektu. Przed zakończeniem aplikacji należy również zapisać ustawienia użytkownika, tak jak w przypadku aplikacji w języku C#. opisano to w poniższej sekcji.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-c"></a>Uzyskiwanie dostępu do lub zmiana ustawień aplikacji w czasie wykonywania w Visual C #
<!-- markdownlint-enable MD003 MD020 -->

W językach innych niż [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , takich jak [!INCLUDE[csprcs](../includes/csprcs-md.md)] , należy uzyskać bezpośredni dostęp do `Settings` klasy, jak pokazano w poniższym [!INCLUDE[csprcs](../includes/csprcs-md.md)] przykładzie.

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

Należy również jawnie wywołać `Save` metodę tej klasy otoki, aby zachować ustawienia użytkownika. Zwykle jest to konieczne w programie `Closing` obsługi zdarzeń formularza głównego. W poniższym [!INCLUDE[csprcs](../includes/csprcs-md.md)] przykładzie pokazano wywołanie `Save` metody.

```csharp
Properties.Settings.Default.Save();
```

Aby uzyskać ogólne informacje na temat uzyskiwania dostępu do ustawień aplikacji za pomocą `Settings` klasy, zobacz [Omówienie ustawień aplikacji](https://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc). Aby uzyskać informacje o iteracji za pomocą ustawień, zobacz ten [wpis na forum](https://social.msdn.microsoft.com/Forums/en-US/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).

## <a name="see-also"></a>Zobacz też

- [Uzyskiwanie dostępu do ustawień aplikacji](https://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e)
