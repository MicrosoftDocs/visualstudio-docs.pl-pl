---
title: Zarządzanie ustawieniami aplikacji (.NET)
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
ms.openlocfilehash: 8d792a6147795f81211203fc442539371f3caa91
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593710"
---
# <a name="manage-application-settings-net"></a>Zarządzanie ustawieniami aplikacji (.NET)

Ustawienia aplikacji umożliwiają dynamiczne przechowywanie informacji o aplikacji. Ustawienia umożliwiają przechowywanie informacji na komputerze klienckim, które nie powinny być zawarte w kodzie aplikacji (na przykład parametry połączenia), preferencjach użytkownika i innych informacjach potrzebnych w czasie wykonywania.

Ustawienia aplikacji zastępują właściwości dynamiczne używane we wcześniejszych wersjach programu Visual Studio.

Każde ustawienie aplikacji musi mieć unikatową nazwę. Nazwa może być dowolną kombinacją liter, cyfr lub podkreślenia, która nie zaczyna się od liczby i nie może mieć spacji. Nazwa zostanie zmieniona `Name` za pośrednictwem właściwości.

Ustawienia aplikacji mogą być przechowywane jako dowolny typ danych, `TypeConverter` który jest `ToString` / `FromString`serializowany do XML lub ma implementuje . Najczęstsze typy `String` `Integer`to `Boolean`, i , ale <xref:System.Drawing.Color>można <xref:System.Object>również przechowywać wartości jako , lub jako parametry połączenia.

Ustawienia aplikacji również posiadają wartość. Wartość jest ustawiana za pomocą **właściwości Value** i musi być zgodna z typem danych ustawienia.

Ponadto ustawienia aplikacji mogą być powiązane z właściwością formularza lub formantu w czasie projektowania.

Istnieją dwa typy ustawień aplikacji, w zależności od zakresu:

- Ustawienia o zakresie aplikacji mogą być używane do informacji, takich jak adres URL usługi sieci web lub parametry połączenia bazy danych. Te wartości są skojarzone z aplikacją. W związku z tym użytkownicy nie można zmienić je w czasie wykonywania.

- Ustawienia o zakresie użytkownika mogą być używane do informacji, takich jak utrwalanie ostatniej pozycji formularza lub preferencji czcionki. Użytkownicy mogą zmieniać te wartości w czasie wykonywania.

Typ ustawienia można zmienić za pomocą właściwości **Scope.**

System projektu przechowuje ustawienia aplikacji w dwóch plikach XML:

- plik *app.config,* który jest tworzony w czasie projektowania podczas tworzenia pierwszego ustawienia aplikacji

- plik *user.config,* który jest tworzony w czasie wykonywania, gdy użytkownik uruchamiany aplikacją zmienia wartość dowolnego ustawienia użytkownika.

Należy zauważyć, że zmiany w ustawieniach użytkownika nie są zapisywane na dysku, chyba że aplikacja specjalnie wywołuje metodę, aby to zrobić.

## <a name="create-application-settings-at-design-time"></a>Tworzenie ustawień aplikacji w czasie projektowania

W czasie projektowania można utworzyć ustawienia aplikacji na dwa sposoby: za pomocą **ustawienia** strony **projektanta projektu**lub za pomocą **właściwości** okna dla formularza lub formantu, który pozwala na powiązanie ustawienia z właściwością.

Podczas tworzenia ustawienia o zakresie aplikacji (na przykład parametry połączenia bazy danych [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lub odwołanie do zasobów serwera), `<applicationSettings>` zapisuje go w *app.config* z tagiem. (Parametry połączenia są zapisywane pod `<connectionStrings>` tagiem).

Podczas tworzenia ustawienia o zakresie użytkownika (na przykład czcionki domyślnej, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] strony głównej lub rozmiaru okna) zapisuje je w *pliku app.config* z tagiem. `<userSettings>`

> [!IMPORTANT]
> Podczas przechowywania ciągów połączeń w *app.config*należy podjąć środki ostrożności, aby uniknąć ujawniania poufnych informacji, takich jak hasła lub ścieżki serwera, w ciągu połączenia.
>
> Jeśli bierzesz informacje o ciągu połączenia ze źródła zewnętrznego, takiego jak użytkownik podający identyfikator użytkownika i hasło, należy zachować ostrożność, aby upewnić się, że wartości używane do konstruowania ciągu połączenia nie zawierają dodatkowych parametrów ciągu połączenia które zmieniają zachowanie połączenia.
>
> Należy rozważyć użycie funkcji Konfiguracja chroniona do szyfrowania poufnych informacji w pliku konfiguracyjnym. Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](/dotnet/framework/data/adonet/protecting-connection-information).

> [!NOTE]
> Ponieważ nie ma modelu pliku konfiguracji dla bibliotek klas, ustawienia aplikacji nie mają zastosowania do projektów biblioteki klas. Wyjątkiem jest projekt Visual Studio Tools for Office DLL, który może mieć plik konfiguracyjny.

## <a name="use-customized-settings-files"></a>Korzystanie z plików ustawień niestandardowych

Można dodać dostosowane pliki ustawień do projektu, aby wygodnie zarządzania grupami ustawień. Ustawienia zawarte w jednym pliku są ładowane i zapisywane jako jednostka. Przechowywanie ustawień w oddzielnych plikach dla często używanych i rzadko używanych grup może zaoszczędzić czas podczas ładowania i zapisywania ustawień.

Na przykład można dodać plik, taki jak *SpecialSettings.settings* do projektu. Chociaż `SpecialSettings` klasa nie jest `My` widoczna w obszarze nazw, program View `Partial Class SpecialSettings` **Code** może odczytać plik ustawień niestandardowych zawierający plik .

**Projektant ustawień** najpierw wyszukuje plik *Settings.settings,* który tworzy system projektu; ten plik jest plikiem domyślnym wyświetlanym przez **projektanta projektu** na karcie **Ustawienia.** *Ustawienia.settings* znajduje [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] się w folderze Mój *projekt* dla [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektów i w folderze *Właściwości* dla projektów. **Projektant projektu** następnie wyszukuje inne pliki ustawień w folderze głównym projektu. W związku z tym należy umieścić plik ustawień niestandardowych tam. Jeśli dodasz plik *.settings* w innym miejscu projektu, **projektant projektu** nie będzie mógł go zlokalizować.

## <a name="access-or-change-application-settings-at-run-time-in-visual-basic"></a>Uzyskiwanie dostępu do ustawień aplikacji lub zmienianie ich w czasie wykonywania w języku Visual Basic

W projektach języka Visual Basic można uzyskać dostęp `My.Settings` do ustawień aplikacji w czasie wykonywania przy użyciu obiektu. Na stronie **Ustawienia** kliknij przycisk **Wyświetl kod,** aby wyświetlić plik *Settings.vb.* *Settings.vb* definiuje `Settings` klasę, która umożliwia obsługę tych zdarzeń w <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>klasie <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>ustawień: , , i <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>. Należy zauważyć, że `Settings` klasa w *Settings.vb* jest klasą częściową, która wyświetla tylko kod należący do użytkownika, a nie całą wygenerowaną klasę. Aby uzyskać więcej informacji na temat `My.Settings` uzyskiwania dostępu do ustawień aplikacji przy użyciu obiektu, zobacz [Access application settings (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Wartości wszystkich ustawień o zakresie użytkownika, które użytkownik zmienia w czasie wykonywania (na przykład położenie formularza) są przechowywane w pliku *user.config.* Zwróć uwagę, że wartości domyślne są nadal zapisywane w *pliku app.config*.

Jeśli wszystkie ustawienia o zakresie użytkownika zostaną zmienione w czasie wykonywania, na przykład podczas testowania aplikacji i chcesz zresetować te ustawienia do wartości domyślnych, kliknij przycisk **Synchronizuj.**

Zdecydowanie zaleca się użycie `My.Settings` obiektu i domyślnego pliku *.settings,* aby uzyskać dostęp do ustawień. Dzieje się tak, ponieważ można użyć **Projektanta ustawień,** aby przypisać właściwości do ustawień, a ponadto ustawienia użytkownika są automatycznie zapisywane przed zamknięciem aplikacji. Jednak aplikacja Visual Basic może uzyskać dostęp do ustawień bezpośrednio. W takim przypadku należy `MySettings` uzyskać dostęp do klasy i użyć niestandardowego pliku *.settings* w katalogu głównym projektu. Należy zapisać ustawienia użytkownika przed zakończeniem aplikacji, tak jak w przypadku aplikacji języka C#; jest to opisane w poniższej sekcji.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="access-or-change-application-settings-at-run-time-in-c"></a>Uzyskiwanie dostępu do ustawień aplikacji lub zmienianie ich w czasie wykonywania w języku C #
<!-- markdownlint-enable MD003 MD020 -->

W językach innych niż Visual Basic, takich jak `Settings` C#, należy uzyskać [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] dostęp do klasy bezpośrednio, jak pokazano w poniższym przykładzie.

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

Należy jawnie wywołać `Save` metodę tej klasy otoki, aby utrwalić ustawienia użytkownika. Zwykle można to `Closing` zrobić w programie obsługi zdarzeń formularza głównego. Poniższy przykład języka C# `Save` pokazuje wywołanie metody.

```csharp
Properties.Settings.Default.Save();
```

Aby uzyskać ogólne informacje dotyczące `Settings` uzyskiwania dostępu do ustawień aplikacji za pośrednictwem klasy, zobacz [Omówienie ustawień aplikacji (.NET Framework)](/dotnet/framework/winforms/advanced/application-settings-overview). Aby uzyskać informacje na temat iteracji w ustawieniach, zobacz ten [post na forum](https://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).

## <a name="see-also"></a>Zobacz też

- [Ustawienia aplikacji programu Access (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
