---
title: Zarządzanie ustawieniami aplikacji (.NET)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e4ea61199159e68f3707b6dac4d3a6c1f5ea7635
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671790"
---
# <a name="manage-application-settings-net"></a>Zarządzanie ustawieniami aplikacji (.NET)

Ustawienia aplikacji umożliwiają przechowywanie informacji o aplikacji dynamicznie. Ustawienia pozwalają na przechowywanie danych na komputerze klienckim, który nie powinny znajdować się w kodzie aplikacji (na przykład parametry połączenia), preferencji użytkownika i innych informacji potrzebnych w czasie wykonywania.

Ustawienia aplikacji zastępują właściwości dynamiczne stosowane we wcześniejszych wersjach programu Visual Studio.

Każde ustawienie aplikacji musi mieć unikatową nazwę. Nazwa może być dowolną kombinacją liter, cyfr lub znaku podkreślenia, która nie rozpoczyna się od numeru i nie może zawierać spacji. Nazwa zostanie zmieniona przez `Name` właściwości.

Ustawienia aplikacji mogą być przechowywane jako dowolny typ danych, który jest serializowany do XML lub `TypeConverter` implementującej `ToString` / `FromString`. Najczęściej używane typy to `String`, `Integer`, i `Boolean`, ale można również przechowywać wartości jako <xref:System.Drawing.Color>, <xref:System.Object>, lub jako parametry połączenia.

Ustawienia aplikacji również zawierającą wartość parametru. Wartość została ustawiona za pomocą **wartość** właściwość musi być zgodny z typem danych ustawienia.

Ponadto ustawienia aplikacji może być powiązana z właściwością formularza lub formantu w czasie projektowania.

Istnieją dwa rodzaje ustawień aplikacji, w oparciu o zakres:

- Ustawienia w zakresie aplikacji może służyć do informacje, takie jak adres URL usługi sieci web lub ciąg połączenia bazy danych. Te wartości są skojarzone z aplikacją. Dlatego użytkownicy nie mogą zmieniać ich w czasie wykonywania.

- Ustawienia z zakresu użytkownika mogą służyć do informacje, np. dotyczących utrwalenia ostatniej pozycji formularza lub preferencji czcionek. Użytkownicy mogą zmieniać te wartości w czasie wykonywania.

Typ ustawienia można zmienić za pomocą **zakres** właściwości.

System projektów przechowuje ustawienia aplikacji w dwóch plikach XML:

- *app.config* pliku, który jest tworzony w czasie projektowania podczas tworzenia pierwszego ustawienia aplikacji

- *user.config* pliku, który jest tworzony w czasie wykonywania, gdy użytkownik uruchamiający aplikację zmienia wartość dowolnego ustawienia użytkownika.

Należy zauważyć, że zmiany w ustawieniach użytkownika nie są zapisywane na dysku, chyba że aplikacja specjalnie wywołuje metodę, aby to zrobić.

## <a name="create-application-settings-at-design-time"></a>Tworzenie ustawień aplikacji w czasie projektowania

W czasie projektowania ustawienia aplikacji można tworzyć na dwa sposoby: za pomocą **ustawienia** strony **projektanta projektu**, lub za pomocą **właściwości** okna formularza lub formant, który pozwala powiązać ustawienie z właściwością.

Podczas tworzenia ustawień o zakresie aplikacji (na przykład parametry połączenia bazy danych lub odwołania do zasobów serwera), [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zapisuje je w *app.config* z `<applicationSettings>` tagu. (Ciągi połączeń są zapisywane w obszarze `<connectionStrings>` tagu.)

Podczas tworzenia ustawień z zakresu użytkownika (na przykład czcionki domyślnej, strony głównej lub rozmiaru okna), [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zapisuje je w *app.config* z `<userSettings>` tagu.

> [!IMPORTANT]
> Jeśli przechowujesz ciągi połączeń w *app.config*, należy podjąć środki ostrożności, aby uniknąć ujawnienia poufnych informacji, takich jak hasła lub ścieżki serwera w parametrach połączenia.
>
> Jeśli nie podejmiesz informacje o parametrach połączenia z zewnętrznego źródła, takiego jak podanie Identyfikatora użytkownika i hasła, należy zachować ostrożność, aby upewnić się, że wartości, które można używać do tworzenia połączenia ciągu nie zawierają dodatkowych parametrów połączenia które zmieniają zachowanie połączenia.
>
> Należy rozważyć użycie funkcji konfiguracji chronionej do szyfrowania poufnych informacji w pliku konfiguracji. Aby uzyskać więcej informacji, zobacz [chronić informacje o połączeniu](/dotnet/framework/data/adonet/protecting-connection-information).

> [!NOTE]
> Ponieważ nie istnieje żaden model pliku konfiguracji dla bibliotek klas, ustawienia aplikacji nie są stosowane do projektów biblioteki klas. Wyjątkiem jest Visual Studio Tools dla pakietu Office DLL projektu, co może mieć plik konfiguracji.

## <a name="use-customized-settings-files"></a>Użyj plików ustawień niestandardowych

Można dodać pliki niestandardowych ustawień do projektu, aby móc wygodniej zarządzać grupami ustawień. Ustawienia, które są zawarte w pojedynczym pliku są ładowane i zapisywane jako jednostka. Przechowywanie ustawień w oddzielnych plikach często używane i rzadko używanych grup może skrócić czas ładowania i zapisywania ustawień.

Na przykład, takich jak możesz dodać plik *SpecialSettings.settings* do projektu. Gdy usługi `SpecialSettings` klasy nie jest widoczny w `My` przestrzeni nazw, **Wyświetl kod** może odczytać plik ustawień niestandardowych, który zawiera `Partial Class SpecialSettings`.

**Projektant ustawień** najpierw szuka *Settings.settings* pliku, który tworzy system projektu; ten plik jest domyślnie pliku, który **projektanta projektu** Wyświetla w **ustawienia** kartę. *Plik Settings.Settings* znajduje się w *mój projekt* folder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektów i *właściwości* folder [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektów. **Projektanta projektu** następnie wyszukuje inne pliki ustawień w folderze głównym projektu. W związku z tym należy umieścić plik ustawień niestandardowych istnieje. Jeśli dodasz *.settings* pliku w innym miejscu w projekcie **projektanta projektu** nie będzie mógł go zlokalizować.

## <a name="access-or-change-application-settings-at-run-time-in-visual-basic"></a>Dostępu lub zmień ustawienia aplikacji w czasie wykonywania w języku Visual Basic

W projektach języka Visual Basic, uzyskujesz dostęp ustawienia aplikacji w czasie wykonywania za pomocą `My.Settings` obiektu. Na **ustawienia** kliknij **wyświetlić kod** przycisk, aby wyświetlić *Settings.vb* pliku. *Settings.VB* definiuje `Settings` klasy, która umożliwia obsługę następujących zdarzeń w klasie ustawień: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>, <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>, <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>, i <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>. Należy zauważyć, że `Settings` klasy w *Settings.vb* jest częściową klasą, która wyświetla tylko włany kod, nie całje wygenerowanej klasy. Aby uzyskać więcej informacji na temat uzyskiwania dostępu do ustawień aplikacji za pomocą `My.Settings` obiektu, zobacz [uzyskać dostęp ustawienia aplikacji (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Wartości ustawienia zakresu użytkownika, które użytkownik zmienia w czasie wykonywania (na przykład położenie formularza) są przechowywane w *user.config* pliku. Należy zauważyć, że wartości domyślne są nadal zapisywane w *app.config*.

Jeśli wszystkie ustawienia z zakresu użytkownika zostały zmienione w czasie wykonywania, na przykład podczas testowania aplikacji i chcesz zresetować te ustawienia do wartości domyślnych, kliknij przycisk **Synchronize** przycisku.

Zdecydowanie zalecamy użycie `My.Settings` obiektu i domyślnego *.settings* pliku ustawień dostępu. To dlatego, możesz użyć **Projektant ustawień** do przypisywania właściwości do ustawienia i, dodatkowo użytkownika ustawienia są zapisywane automatycznie przed zamknięciem aplikacji. Jednak aplikacji Visual Basic można uzyskiwać dostęp do ustawień bezpośrednio. W takim przypadku musisz uzyskać dostęp `MySettings` klasy i użyć niestandardowego *.settings* plik w folderze głównym projektu. Musisz zapisać ustawienia użytkownika przed zakończeniem aplikacji, tak jak w języku C# aplikacji; jest to opisane w poniższej sekcji.

## <a name="access-or-change-application-settings-at-run-time-in-c"></a>Dostępu lub zmień ustawienia aplikacji w czasie wykonywania w języku C# #

W językach innych niż Visual Basic, takich jak C#, należy przejść do `Settings` klasy bezpośrednio, jak pokazano w następującym [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] przykład.

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

Należy jawnie wywołać `Save` metody tej klasy otoki, aby utrwalić ustawienia użytkownika. Zwykle to zrobić w `Closing` programu obsługi zdarzeń formularza głównego. Poniższy przykład C# pokazuje wywołanie `Save` metody.

```csharp
Properties.Settings.Default.Save();
```

Aby uzyskać ogólne informacje na temat uzyskiwania dostępu do ustawień aplikacji za pomocą `Settings` klasy, zobacz [Przegląd ustawień aplikacji (.NET Framework)](/dotnet/framework/winforms/advanced/application-settings-overview). Aby uzyskać informacje o iterowaniu przez ustawienia, zobacz ten [wpis na forum](https://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).

## <a name="see-also"></a>Zobacz także

- [Dostęp do ustawień aplikacji (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
