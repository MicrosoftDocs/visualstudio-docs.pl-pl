---
title: Strona usług, Projektant projektu
ms.date: 06/14/2018
ms.topic: reference
f1_keywords:
- ApplicationSettingsOverview
helpviewer_keywords:
- Settings page in Project Designer
- Project Designer, Settings page
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f4ca1def334241999445e3f11cf142aa426d962
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566777"
---
# <a name="settings-page-project-designer"></a>Strona Ustawienia, Projektant projektu

Użyj **strony Ustawienia** projektanta projektu, aby określić ustawienia aplikacji projektu. Ustawienia aplikacji umożliwiają dynamiczne przechowywanie i pobieranie ustawień właściwości i innych informacji dla aplikacji. Umożliwiają one również obsługę niestandardowych aplikacji i preferencji użytkownika na komputerze klienckim. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji](../managing-application-settings-dotnet.md).

Aby uzyskać dostęp do strony **Ustawienia,** wybierz węzeł projektu w **Eksploratorze rozwiązań,** a następnie wybierz pozycję**Właściwości** **projektu** > . Po wyświetleniu projektanta projektu wybierz kartę **Ustawienia.**

## <a name="header-bar"></a>Pasek nagłówka

Pasek nagłówka w górnej części strony **Ustawienia** zawiera kilka kontrolek:

**Synchronizacji**

**Synchronizacja** przywraca ustawienia o zakresie użytkownika używane przez aplikację w czasie wykonywania lub podczas debugowania do ich wartości domyślnych zdefiniowanych w czasie projektowania. Aby przywrócić dane, usuń pliki specyficzne dla aplikacji generowane w czasie wykonywania z dysku, a nie z danych projektu.

**Załaduj ustawienia sieci Web**

**Załaduj ustawienia sieci Web** wyświetla okno dialogowe **Logowanie,** które umożliwia ładowanie ustawień dla uwierzytelnionego użytkownika lub dla użytkowników anonimowych. Ten przycisk jest włączony tylko wtedy, gdy włączono usługi aplikacji klienckich na stronie **Usługi** i określono **lokalizację usługi ustawień sieci Web**.

**Wyświetl kod**

W przypadku projektów języka C# przycisk **Wyświetl kod** umożliwia wyświetlanie kodu w pliku *Settings.cs.* Ten plik definiuje `Settings` klasę, która umożliwia obsługę określonych `Settings` zdarzeń na obiekcie. W językach innych niż Visual Basic należy `Save` jawnie wywołać metodę tej klasy otoki, aby utrwalić ustawienia użytkownika. Zwykle to zrobić w **closing** obsługi zdarzenia formularza głównego. Poniżej znajduje się przykład `Save` wywołania metody:

```csharp
Properties.Settings.Default.Save();
```

W przypadku projektów języka Visual Basic przycisk **Wyświetl kod** umożliwia wyświetlenie kodu w pliku *Settings.vb.* Ten plik definiuje `MySettings` klasę, która umożliwia obsługę określonych `My.Settings` zdarzeń na obiekcie. Aby uzyskać więcej informacji na temat `My.Settings` uzyskiwania dostępu do ustawień aplikacji przy użyciu obiektu, zobacz [Ustawienia aplikacji programu Access](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Aby uzyskać więcej informacji na temat uzyskiwania dostępu do ustawień aplikacji, zobacz [Ustawienia aplikacji dla formularzy systemu Windows](/dotnet/framework/winforms/advanced/application-settings-for-windows-forms).

**Modyfikator dostępu**

Przycisk **modyfikatora programu Access** określa `Properties.Settings` poziom dostępu klas `My.Settings` pomocniczych (w języku C#) lub (w języku Visual Basic), które program Visual Studio generuje w *Settings.Designer.cs* lub *Settings.Designer.vb*.

W przypadku projektów programu Visual C# modyfikator dostępu może być **wewnętrzny** lub **publiczny**.

W przypadku projektów języka Visual Basic modyfikator dostępu może być **przyjazny** lub **publiczny.**

Domyślnie ustawienie jest **wewnętrzne** w języku C# i **Przyjaciel** w języku Visual Basic. Gdy program Visual Studio generuje klasy pomocnicze jako **wewnętrzne** lub **znajome,** aplikacje wykonywalne (*.exe*) nie mogą uzyskać dostępu do zasobów i ustawień dodanych do bibliotek klas ( pliki*dll).* Jeśli musisz udostępnić zasoby i ustawienia z biblioteki klas, ustaw modyfikator dostępu na **Public**.

Aby uzyskać więcej informacji na temat klas pomocnika ustawień, zobacz [Zarządzanie ustawieniami aplikacji](../managing-application-settings-dotnet.md).

## <a name="settings-grid"></a>Siatka ustawień

**Siatka ustawień** służy do konfigurowania ustawień aplikacji. Ta siatka zawiera następujące kolumny:

**Nazwa**

W tym polu należy wprowadzić nazwę ustawienia aplikacji.

**Typ**

Użyj listy rozwijanej, aby wybrać typ dla tego ustawienia. Najczęściej używane typy pojawiają się na liście rozwijanej, na przykład **Ciąg ,** **(Parametry połączenia)** i **System.Drawing.Font**. Możesz wybrać inny typ, wybierając **pozycję Przeglądaj** na końcu listy, a następnie wybierając typ z okna **dialogowego Wybieranie typu.** Po wybraniu typu jest on dodawany do typowych typów na liście rozwijanej (tylko dla bieżącego rozwiązania).

**Zakres**

Wybierz **aplikację** lub **użytkownika**.

Ustawienia o zakresie aplikacji, takie jak parametry połączenia, są skojarzone z aplikacją. Użytkownicy nie mogą zmieniać ustawień o zakresie aplikacji w czasie wykonywania.

Ustawienia o zakresie użytkownika, takie jak czcionki systemowe, są przeznaczone do użycia w preferencjach użytkownika. Użytkownicy mogą je zmieniać w czasie wykonywania.

**Wartość**

Dane lub wartość skojarzona z ustawieniem aplikacji. Na przykład, jeśli ustawienie jest czcionką, jego wartością może być **Verdana, 9.75pt, style=Bold**.

## <a name="see-also"></a>Zobacz też

- [Zarządzanie ustawieniami aplikacji](../managing-application-settings-dotnet.md)
- [Ustawienia aplikacji programu Access (Visual Basic)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
