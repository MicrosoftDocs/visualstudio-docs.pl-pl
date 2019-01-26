---
title: Strona usług, Projektant projektu
ms.date: 06/14/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ApplicationSettingsOverview
helpviewer_keywords:
- Settings page in Project Designer
- Project Designer, Settings page
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fee0e6539901e5b95ca62f5e2beb1c3ea48692b0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958619"
---
# <a name="settings-page-project-designer"></a>Strona Ustawienia, Projektant projektu

Użyj **ustawienia** strony projektanta projektu, aby określić ustawienia aplikacji projektu. Ustawienia aplikacji umożliwiają przechowywanie i pobieranie ustawień właściwości i inne informacje o aplikacji dynamicznie. Umożliwiają one również utrzymania niestandardowych aplikacji i preferencji użytkowników na komputerze klienckim. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji](../managing-application-settings-dotnet.md).

Aby uzyskać dostęp do **ustawienia** wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie wybierz pozycję **projektu** > **właściwości**. Gdy pojawi się w Projektancie projektu, wybierz **ustawienia** kartę.

## <a name="header-bar"></a>Pasku nagłówka

Na pasku nagłówka, w górnej części **ustawienia** strona zawiera kilka kontrolek:

**Synchronizuj**

**Synchronizuj** przywrócenie ustawień zakresu użytkownika, których korzysta aplikacja, w czasie wykonywania, czy podczas debugowania do wartości domyślnych, zgodnie z definicją w czasie projektowania. Aby przywrócić dane, Usuń środowiska wykonawczego wygenerowanych plików specyficznych dla aplikacji, z dysku, a nie z danych projektu.

**Załaduj ustawienia sieci Web**

**Załaduj ustawienia sieci Web** Wyświetla **logowania** okno dialogowe, które umożliwia ładowanie ustawień dla uwierzytelnionego użytkownika lub dla użytkowników anonimowych. Ten przycisk jest aktywny tylko wtedy, gdy włączono usługi aplikacji klienta na **usług** strony, a określone **ustawienia sieci Web usługi lokalizacji**.

**Wyświetl kod**

Dla projektów C# **Wyświetl kod** przycisk umożliwia wyświetlenie kodu w *Settings.cs* pliku. Ten plik definiuje `Settings` klasy, która umożliwia obsługę określonych zdarzeń w `Settings` obiektu. W językach innych niż Visual Basic, należy jawnie wywołać `Save` metody tej klasy otoki, aby utrwalić ustawienia użytkownika. Zwykle to zrobić w **zamykanie** program obsługi zdarzeń formularza głównego. Poniżej znajduje się przykład wywołania `Save` metody:

```csharp
Properties.Settings.Default.Save();
```

W przypadku projektów Visual Basic **Wyświetl kod** przycisk umożliwia wyświetlenie kodu w *Settings.vb* pliku. Ten plik definiuje `MySettings` klasy, która umożliwia obsługę określonych zdarzeń w `My.Settings` obiektu. Aby uzyskać więcej informacji na temat uzyskiwania dostępu do ustawień aplikacji za pomocą `My.Settings` obiektu, zobacz [dostęp do ustawień aplikacji](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Aby uzyskać więcej informacji na temat uzyskiwania dostępu do ustawień aplikacji, zobacz [ustawienia aplikacji dla formularzy Windows Forms](/dotnet/framework/winforms/advanced/application-settings-for-windows-forms).

**Modyfikator dostępu**

**Modyfikator dostępu** przycisk określa poziom dostępu `Properties.Settings` (w języku C#) lub `My.Settings` (w języku Visual Basic) pomocnicze klasy, które program Visual Studio generuje w *Settings.Designer.cs* lub *Settings.Designer.vb*.

W projektach Visual C#, może być modyfikator dostępu **wewnętrzne** lub **publicznych**.

W przypadku projektów Visual Basic, może być modyfikator dostępu **Friend** lub **publicznych**.

Domyślnym ustawieniem jest **wewnętrzne** w języku C# i **Friend** w języku Visual Basic. Gdy program Visual Studio generuje klasy pomocnika jako **wewnętrzne** lub **Friend**wykonywalnym (*.exe*) aplikacje nie mogą uzyskiwać dostęp do zasobów i ustawienia, które zostały dodane do klasy biblioteki (*.dll* plików). Jeśli masz na udostępnianie zasobów i ustawień z biblioteki klas, ustaw modyfikator dostępu **publicznych**.

Aby uzyskać więcej informacji na temat ustawień klasy pomocnika, zobacz [Zarządzanie ustawieniami aplikacji](../managing-application-settings-dotnet.md).

## <a name="settings-grid"></a>Ustawienia siatki

**Ustawienia siatki** służy do konfigurowania ustawień aplikacji. Ta siatka zawiera następujące kolumny:

**Nazwa**

Wprowadź nazwę ustawienia aplikacji, w tym polu.

**Typ**

Użyj listy rozwijanej, aby wybrać typ ustawienia. Najczęściej używane typy są wyświetlane na liście rozwijanej, na przykład **ciąg**, **(parametry połączenia)**, i **System.Drawing.Font**. Można wybrać inny typ, wybierając **Przeglądaj** na końcu listy, a następnie wybierając typ z **wybierz typ** okno dialogowe. Po wybraniu typu, dodaniu popularnych typów (dla bieżącego rozwiązania tylko) na liście rozwijanej.

**Zakres**

Wybierz opcję **aplikacji** lub **użytkownika**.

Ustawienia w zakresie aplikacji, takich jak parametry połączenia są skojarzone z aplikacją. Użytkownicy nie mogą zmieniać ustawienia w zakresie aplikacji w czasie wykonywania.

Ustawienia z zakresu użytkownika, takie jak czcionki systemowe są przeznaczone do użytku z preferencji użytkownika. Użytkownicy mogą zmieniać ich w czasie wykonywania.

**Wartość**

Dane lub wartość skojarzoną z ustawienia aplikacji. Na przykład, jeśli to ustawienie ma czcionkę, jego wartość może być **Verdana, 9.75pt, styl pogrubiony =**.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie ustawieniami aplikacji](../managing-application-settings-dotnet.md)
- [Dostęp do ustawień aplikacji (Visual Basic)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)