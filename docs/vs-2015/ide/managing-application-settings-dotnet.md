---
title: Zarządzanie ustawieniami aplikacji (.NET) | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a2d5d5ff514752234bba3020927716d57ee413d1
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54793289"
---
# <a name="managing-application-settings-net"></a>Zarządzanie ustawieniami aplikacji (.NET)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ustawienia aplikacji umożliwiają przechowywanie informacji o aplikacji dynamicznie. Ustawienia pozwalają na przechowywanie danych na komputerze klienckim, który nie powinny znajdować się w kodzie aplikacji (na przykład parametry połączenia), preferencji użytkownika i innych informacji potrzebnych w czasie wykonywania.  
  
 Ustawienia aplikacji zastępują właściwości dynamiczne stosowane we wcześniejszych wersjach programu Visual Studio.  
  
 Każde ustawienie aplikacji musi mieć unikatową nazwę. Nazwa może być dowolną kombinacją liter, cyfr lub znaku podkreślenia, która nie rozpoczyna się od numeru i nie może zawierać spacji. Nazwę można zmienić, modyfikując `Name` właściwości.  
  
 Ustawienia aplikacji mogą być przechowywane jako dowolny typ danych, który może być serializowany do XML lub `TypeConverter` implementującej `ToString` / `FromString`. Najczęściej używane typy to `String`, `Integer`, i `Boolean`, ale można również przechowywać wartości jako <xref:System.Drawing.Color>, <xref:System.Object>, lub jako parametry połączenia.  
  
 Ustawienia aplikacji również zawierają wartość. Wartość została ustawiona za pomocą **wartość** właściwość musi być zgodny z typem danych ustawienia.  
  
 Ponadto ustawienia aplikacji może być powiązana z właściwością formularza lub formantu w czasie projektowania.  
  
 Istnieją dwa rodzaje ustawień aplikacji, w oparciu o zakres:  
  
- Ustawienia w zakresie aplikacji może służyć do informacje, takie jak adres URL usługi sieci Web lub ciąg połączenia bazy danych. Te wartości są skojarzone z aplikacją. Dlatego użytkownicy nie mogą zmieniać ich w czasie wykonywania.  
  
- Ustawienia z zakresu użytkownika mogą służyć do informacje, np. dotyczących utrwalenia ostatniej pozycji formularza lub preferencji czcionek. Użytkownicy mogą zmieniać te wartości w czasie wykonywania.  
  
  Typ ustawienia można zmienić za pomocą **zakres** właściwości.  
  
  System projektów przechowuje ustawienia aplikacji w dwóch plikach XML: pliku app.config, który jest tworzony w czasie projektowania podczas tworzenia pierwszego ustawienia aplikacji; i w pliku user.config, który jest tworzony w czasie wykonywania, gdy użytkownik uruchamiający aplikację zmienia wartość dowolnego ustawienia użytkownika. Należy zauważyć, że zmiany w ustawieniach użytkownika nie są zapisywane na dysku, chyba że aplikacja specjalnie wywołuje metodę, aby to zrobić.  
  
## <a name="creating-application-settings-at-design-time"></a>Tworzenie ustawień aplikacji w czasie projektowania  
 W czasie projektowania ustawienia aplikacji można tworzyć na dwa sposoby: za pomocą **ustawienia** strony **projektanta projektu**, lub za pomocą **właściwości** okna formularza lub formant, który pozwala powiązać ustawienie z właściwością.  
  
 Podczas tworzenia ustawień o zakresie aplikacji (na przykład parametry połączenia bazy danych lub odwołania do zasobów serwera), [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zapisuje je w pliku app.config przy użyciu `<applicationSettings>` tagu. (Ciągi połączeń są zapisywane w obszarze `<connectionStrings>` tagu.)  
  
 Podczas tworzenia ustawień z zakresu użytkownika (na przykład czcionki domyślnej, strony głównej lub rozmiaru okna), [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zapisuje je w pliku app.config przy użyciu `<userSettings>` tagu.  
  
> [!IMPORTANT]
>  Kiedy przechowujesz ciągi połączeń w pliku app.config, należy podjąć środki ostrożności, aby uniknąć ujawnienia poufnych informacji, takich jak hasła lub ścieżki serwera w parametrach połączenia.  
>   
>  Jeśli nie podejmiesz informacje o parametrach połączenia z zewnętrznego źródła, takiego jak podanie Identyfikatora użytkownika i hasła, należy zachować ostrożność, aby upewnić się, że wartości, które można używać do tworzenia połączenia ciągu nie zawierają dodatkowych parametrów połączenia które zmieniają zachowanie połączenia.  
>   
>  Należy rozważyć użycie funkcji konfiguracji chronionej do szyfrowania poufnych informacji w pliku konfiguracji. Zobacz [ochrony informacji o połączeniu](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4) Aby uzyskać więcej informacji.  
  
> [!NOTE]
>  Ponieważ nie istnieje żaden model pliku konfiguracji dla bibliotek klas, ustawienia aplikacji nie są stosowane do projektów biblioteki klas. Wyjątkiem jest Visual Studio Tools dla pakietu Office DLL projektu, co może mieć plik konfiguracji.  
  
## <a name="using-customized-settings-files"></a>Przy użyciu plików ustawień niestandardowych  
 Można dodać pliki niestandardowych ustawień do projektu, aby móc wygodniej zarządzać grupami ustawień. Ustawienia, które są zawarte w pojedynczym pliku są ładowane i zapisywane jako jednostka. Dlatego możliwość ustawienia są przechowywane w oddzielnych plikach dla często i rzadko używanych grup może skrócić czas ładowania i zapisywania ustawień.  
  
 Na przykład można dodać plik taki jak SpecialSettings.settings do swojego projektu. Gdy usługi `SpecialSettings` klasy nie jest widoczny w `My` przestrzeni nazw, **Wyświetl kod** może odczytać plik ustawień niestandardowych, który zawiera `Partial Class SpecialSettings`.  
  
 Projektant ustawień najpierw szuka pliku Settings.settings, który tworzy system projektu; jest to domyślny plik, który wyświetla w Projektancie projektu **ustawienia** kartę. Plik Settings.Settings znajduje się w folderze Mój projekt [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projekty w folderze właściwości w przypadku [!INCLUDE[csprcs](../includes/csprcs-md.md)] projektów. Następnie Projektant projektu wyszukuje inne pliki ustawień w folderze głównym projektu. W związku z tym należy umieścić plik ustawień niestandardowych istnieje. Po dodaniu pliku .settings w innym miejscu w projekcie Projektant projektu nie będzie można go znaleźć.  
  
## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-basic"></a>Uzyskiwanie dostępu do lub zmiana ustawień aplikacji w czasie wykonywania w języku Visual Basic  
 W [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projektów, mieli dostęp ustawienia aplikacji w czasie wykonywania za pomocą `My.Settings` obiektu. Na **ustawienia** kliknij **wyświetlić kod** przycisk, aby wyświetlić plik Settings.vb. Plik Settings.VB definiuje `Settings` klasy, która umożliwia obsługę następujących zdarzeń w klasie ustawień: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>, <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>, <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>, i <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>. Należy zauważyć, że `Settings` klasa w Settings.vb jest częściową klasą, która wyświetla tylko włany kod, nie całje wygenerowanej klasy. Aby uzyskać więcej informacji na temat uzyskiwania dostępu do ustawień aplikacji za pomocą `My.Settings` obiektu, zobacz [uzyskiwania dostępu do ustawień aplikacji](http://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e).  
  
 Wartości ustawienia zakresu użytkownika, które użytkownik zmienia w czasie wykonywania (na przykład położenie formularza) są przechowywane w pliku user.config. Należy zauważyć, że wartości domyślne są nadal zapisywane w pliku app.config.  
  
 Jeśli zmieniono żadnych ustawień zakresu użytkownika w czasie wykonywania, na przykład podczas testowania aplikacji, a chcesz zresetować te ustawienia do wartości domyślnych, kliknij przycisk **Synchronize** przycisku.  
  
 Zdecydowanie zalecamy użycie `My.Settings` obiektu i domyślnego pliku .settings do ustawień dostępu. Jest to spowodowane Projektant ustawień służy do przypisywania właściwości do ustawienia, a ponadto ustawienia użytkownika są zapisywane automatycznie przed zamknięciem aplikacji. Jednak Twoja [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] aplikacja może uzyskiwać dostęp do ustawień bezpośrednio. W takim przypadku musisz uzyskać dostęp `MySettings` klasy i użyć pliku niestandardowego .settings w katalogu głównym projektu. Należy również zapisać ustawienia użytkownika przed zakończeniem aplikacji, tak jak w języku C# aplikacji; jest to opisane w poniższej sekcji.  
  
## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-c"></a>Uzyskiwanie dostępu do lub zmiana ustawień aplikacji w czasie wykonywania w Visual C#  
 W językach innych niż [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], takich jak [!INCLUDE[csprcs](../includes/csprcs-md.md)], należy przejść do `Settings` klasy bezpośrednio, jak pokazano w następującym [!INCLUDE[csprcs](../includes/csprcs-md.md)] przykład.  
  
```csharp  
Properties.Settings.Default.FirstUserSetting = "abc";  
```  
  
 Należy także jawnie wywołać `Save` metody tej klasy otoki, aby utrwalić ustawienia użytkownika. Zwykle to zrobić w `Closing` programu obsługi zdarzeń formularza głównego. Następujące [!INCLUDE[csprcs](../includes/csprcs-md.md)] przykład ilustruje sposób wywoływania `Save` metody.  
  
```csharp  
Properties.Settings.Default.Save();  
```  
  
 Aby uzyskać ogólne informacje na temat uzyskiwania dostępu do ustawień aplikacji za pomocą `Settings` klasy, zobacz [Przegląd ustawień aplikacji](http://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc). Aby uzyskać informacje o iterowaniu przez ustawienia, zobacz ten [wpis na forum](http://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do ustawień aplikacji](http://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e)
