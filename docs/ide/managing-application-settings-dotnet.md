---
title: Zarządzanie ustawieniami aplikacji (.NET)
description: Dowiedz się, jak zarządzać ustawieniami aplikacji (dawniej nazywanymi właściwościami dynamicznymi), które nie są uwzględnione w kodzie aplikacji, ale są wymagane w czasie wykonywania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f62e03210e83f434bd32d08c3fe0f7b2b539155e
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596901"
---
# <a name="manage-application-settings-net"></a>Zarządzanie ustawieniami aplikacji (.NET)

Ustawienia aplikacji umożliwiają dynamiczne przechowywanie informacji o aplikacji. Ustawienia umożliwiają przechowywanie na komputerze klienckim informacji, które nie powinny być uwzględniane w kodzie aplikacji (na przykład parametrów połączenia), preferencjach użytkownika i innych informacji potrzebnych w czasie wykonywania.

Ustawienia aplikacji zastępują właściwości dynamiczne używane we wcześniejszych wersjach programu Visual Studio.

Każde ustawienie aplikacji musi mieć unikatową nazwę. Nazwa może być dowolną kombinacją liter, cyfr lub znaku podkreślenia, który nie zaczyna się od cyfry i nie może zawierać spacji. Nazwa zostanie zmieniona przez `Name` Właściwość.

Ustawienia aplikacji mogą być przechowywane jako dowolny typ danych, który jest serializowany do XML lub ma `TypeConverter` zaimplementowany `ToString` / `FromString` . Najczęściej używane typy to `String` , `Integer` , i `Boolean` , ale można również przechowywać wartości jako <xref:System.Drawing.Color> <xref:System.Object> Parametry połączenia.

Ustawienia aplikacji również przechowują wartość. Wartość jest ustawiana za pomocą właściwości **Value** i musi być zgodna z typem danych ustawienia.

Ponadto ustawienia aplikacji mogą być powiązane z właściwością formularza lub kontrolki w czasie projektowania.

Istnieją dwa typy ustawień aplikacji na podstawie zakresu:

- Ustawienia zakresu aplikacji mogą służyć jako informacje takie jak adres URL dla usługi sieci Web lub parametry połączenia z bazą danych. Te wartości są skojarzone z aplikacją. W związku z tym użytkownicy nie mogą zmienić ich w czasie wykonywania.

- Ustawienia o zakresie użytkownika mogą służyć do takich informacji, jak utrwalanie ostatniej pozycji formularza lub preferencji czcionki. Użytkownicy mogą zmieniać te wartości w czasie wykonywania.

Typ ustawienia można zmienić za pomocą właściwości **SCOPE** .

System projektu przechowuje ustawienia aplikacji w dwóch plikach XML:

- plik *app.config* , który jest tworzony w czasie projektowania podczas tworzenia pierwszego ustawienia aplikacji

- plik *user.config* , który jest tworzony w czasie wykonywania, gdy użytkownik, który uruchamia aplikację, zmienia wartość dowolnego ustawienia użytkownika.

Zwróć uwagę, że zmiany ustawień użytkownika nie są zapisywane na dysku, chyba że aplikacja wywołuje metodę, aby to zrobić.

## <a name="create-application-settings-at-design-time"></a>Tworzenie ustawień aplikacji w czasie projektowania

W czasie projektowania można utworzyć ustawienia aplikacji na dwa sposoby: za pomocą strony **Ustawienia** **projektanta projektu** lub za pomocą okna **Właściwości** formularza lub kontrolki, co pozwala powiązać ustawienie z właściwością.

W przypadku tworzenia ustawienia o zakresie aplikacji (na przykład parametrów połączenia z bazą danych lub odwołania do zasobów serwera) program [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zapisuje je w *app.config* przy użyciu `<applicationSettings>` znacznika. (Parametry połączenia są zapisywane pod `<connectionStrings>` tagiem).

Podczas tworzenia ustawienia o zakresie użytkownika (na przykład czcionki domyślnej, strony głównej lub rozmiaru okna), program [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zapisuje ją w *app.config* przy użyciu `<userSettings>` znacznika.

> [!IMPORTANT]
> W przypadku przechowywania parametrów połączenia w *app.config* należy podjąć odpowiednie środki ostrożności, aby uniknąć ujawnienia poufnych informacji, takich jak hasła lub ścieżki serwera, w parametrach połączenia.
>
> W przypadku korzystania z informacji o parametrach połączenia z zewnętrznego źródła, takiego jak podanie identyfikatora użytkownika i hasła, należy zachować ostrożność, aby upewnić się, że wartości używane do konstruowania parametrów połączenia nie zawierają dodatkowych parametrów połączenia, które zmieniają zachowanie połączenia.
>
> Rozważ użycie funkcji konfiguracja chroniona do szyfrowania poufnych informacji w pliku konfiguracji. Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](/dotnet/framework/data/adonet/protecting-connection-information).

> [!NOTE]
> Ponieważ nie istnieje model plików konfiguracji dla bibliotek klas, ustawienia aplikacji nie są stosowane dla projektów biblioteki klas. Wyjątkiem jest Visual Studio Tools projektu DLL pakietu Office, który może mieć plik konfiguracji.

## <a name="use-customized-settings-files"></a>Użyj niestandardowych plików ustawień

Możesz dodać dostosowane pliki ustawień do projektu, aby wygodnie zarządzać grupami ustawień. Ustawienia, które są zawarte w pojedynczym pliku, są ładowane i zapisywane jako jednostka. Przechowywanie ustawień w oddzielnych plikach dla często używanych i rzadko używanych grup może zaoszczędzić czas podczas ładowania i zapisywania ustawień.

Na przykład można dodać do projektu plik, taki jak *SpecialSettings. Settings* . Gdy `SpecialSettings` Klasa nie jest ujawniona w `My` przestrzeni nazw, **Wyświetl kod** może odczytać plik ustawień niestandardowych, który zawiera `Partial Class SpecialSettings` .

**Projektant ustawień** najpierw szuka pliku *Settings. Settings* tworzonego przez system projektu; Ten plik jest domyślnym plikiem, który **Projektant projektu** wyświetla na karcie **Ustawienia** . *Ustawienia. ustawienia* znajdują się w folderze *My Project* dla [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektów i w folderze *Właściwości* dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektów. **Projektant projektu** następnie wyszukuje inne pliki ustawień w folderze głównym projektu. W związku z tym należy umieścić w tym miejscu plik ustawień niestandardowych. Jeśli dodasz plik *. Settings* w innym miejscu projektu, **Projektant projektu** nie będzie mógł go zlokalizować.

## <a name="access-or-change-application-settings-at-run-time-in-visual-basic"></a>Dostęp lub zmiana ustawień aplikacji w czasie wykonywania w Visual Basic

W projektach Visual Basic można uzyskać dostęp do ustawień aplikacji w czasie wykonywania przy użyciu `My.Settings` obiektu. Na stronie **Ustawienia** kliknij przycisk **Wyświetl kod** , aby wyświetlić plik *Settings. vb* . *Settings. vb* definiuje `Settings` klasę, która umożliwia obsługę tych zdarzeń w klasie Settings: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> , <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged> , <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded> i <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> . Należy zauważyć, że `Settings` Klasa w *Settings. vb* jest klasą częściową, która wyświetla tylko kod należący do użytkownika, a nie całą wygenerowaną klasę. Aby uzyskać więcej informacji na temat uzyskiwania dostępu do ustawień aplikacji za pomocą `My.Settings` obiektu, zobacz [dostęp do ustawień aplikacji (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Wartości wszelkich ustawień o zakresie użytkownika, które użytkownik zmienia w czasie wykonywania (na przykład pozycja formularza), są przechowywane w pliku *user.config* . Zwróć uwagę, że wartości domyślne są nadal zapisywane w *app.config*.

Jeśli jakiekolwiek ustawienia o zakresie użytkownika zostaną zmienione w czasie wykonywania, na przykład w testowaniu aplikacji i chcesz zresetować te ustawienia do wartości domyślnych, kliknij przycisk **Synchronizuj** .

Zdecydowanie zalecamy użycie `My.Settings` obiektu i domyślnego pliku *. Settings* w celu uzyskania dostępu do ustawień. Jest to spowodowane tym, że można użyć **projektanta ustawień** do przypisywania właściwości do ustawień, a ponadto ustawienia użytkownika zostaną automatycznie zapisane przed zamknięciem aplikacji. Jednak aplikacja Visual Basic może uzyskać dostęp do ustawień bezpośrednio. W takim przypadku musisz uzyskać dostęp do `MySettings` klasy i użyć pliku Custom *. Settings* w katalogu głównym projektu. Przed zakończeniem aplikacji należy zapisać ustawienia użytkownika, tak jak w przypadku aplikacji C#; opisano to w poniższej sekcji.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="access-or-change-application-settings-at-run-time-in-c"></a>Dostęp lub zmiana ustawień aplikacji w czasie wykonywania w języku C #
<!-- markdownlint-enable MD003 MD020 -->

W językach innych niż Visual Basic, takich jak C#, należy uzyskać bezpośredni dostęp do `Settings` klasy, jak pokazano w poniższym [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] przykładzie.

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

Należy jawnie wywołać `Save` metodę tej klasy otoki, aby zachować ustawienia użytkownika. Zwykle jest to konieczne w programie `Closing` obsługi zdarzeń formularza głównego. W poniższym przykładzie w języku C# pokazano wywołanie `Save` metody.

```csharp
Properties.Settings.Default.Save();
```

Aby uzyskać ogólne informacje na temat uzyskiwania dostępu do ustawień aplikacji za pomocą `Settings` klasy, zobacz [Omówienie ustawień aplikacji (.NET Framework)](/dotnet/framework/winforms/advanced/application-settings-overview). Aby uzyskać informacje o iteracji za pomocą ustawień, zobacz ten [wpis na forum](https://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).

## <a name="see-also"></a>Zobacz także

- [Dostęp do ustawień aplikacji (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
