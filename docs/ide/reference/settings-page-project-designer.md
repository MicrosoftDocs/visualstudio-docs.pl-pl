---
title: Strona usług, Projektant projektu
ms.date: 06/14/2018
ms.topic: reference
f1_keywords:
- ApplicationSettingsOverview
helpviewer_keywords:
- Settings page in Project Designer
- Project Designer, Settings page
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11f6f787d3799813aa526395a7137fd68e5c573d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645262"
---
# <a name="settings-page-project-designer"></a>Strona Ustawienia, Projektant projektu

Użyj strony **Ustawienia** projektanta projektu, aby określić ustawienia aplikacji projektu. Ustawienia aplikacji umożliwiają dynamiczne przechowywanie i pobieranie ustawień właściwości oraz innych informacji dotyczących aplikacji. Umożliwiają one również obsługę niestandardowych preferencji aplikacji i użytkowników na komputerze klienckim. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji](../managing-application-settings-dotnet.md).

Aby uzyskać dostęp do strony **Ustawienia** , wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie wybierz pozycję **Project**  > **Właściwości**. Gdy zostanie wyświetlony Projektant projektu, wybierz kartę **Ustawienia** .

## <a name="header-bar"></a>Pasek nagłówka

Pasek nagłówka w górnej części strony **Ustawienia** zawiera kilka kontrolek:

**Zsynchronizuj**

Funkcja **Synchronizuj** przywraca ustawienia o zakresie użytkownika, które są używane przez aplikację w czasie wykonywania lub podczas debugowania, zgodnie z wartościami domyślnymi zdefiniowanymi w czasie projektowania. Aby przywrócić dane, Usuń pliki specyficzne dla aplikacji w czasie wykonywania z dysku, a nie z danych projektu.

**Załaduj ustawienia sieci Web**

**Okno dialogowe** **ładowanie ustawień sieci Web** umożliwia załadowanie ustawień dla uwierzytelnionego użytkownika lub użytkowników anonimowych. Ten przycisk jest włączony tylko wtedy, gdy włączono usługi aplikacji klienta na stronie **usługi** i określono **lokalizację usługi ustawień sieci Web**.

**Wyświetl kod**

W C# przypadku projektów przycisk **Wyświetl kod** umożliwia wyświetlenie kodu w pliku *Settings.cs* . Ten plik definiuje klasę `Settings`, która umożliwia obsługę określonych zdarzeń w obiekcie `Settings`. W językach innych niż Visual Basic należy jawnie wywołać metodę `Save` tej klasy otoki, aby zachować ustawienia użytkownika. Zwykle jest to konieczne w procedurze obsługi zdarzeń **zamykających** w formularzu głównym. Poniżej znajduje się przykład wywołania metody `Save`:

```csharp
Properties.Settings.Default.Save();
```

W przypadku projektów Visual Basic przycisk **Wyświetl kod** umożliwia wyświetlenie kodu w pliku *Settings. vb* . Ten plik definiuje klasę `MySettings`, która umożliwia obsługę określonych zdarzeń w obiekcie `My.Settings`. Aby uzyskać więcej informacji na temat uzyskiwania dostępu do ustawień aplikacji za pomocą obiektu `My.Settings`, zobacz [dostęp do ustawień aplikacji](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Aby uzyskać więcej informacji na temat uzyskiwania dostępu do ustawień aplikacji, zobacz [Ustawienia aplikacji dla Windows Forms](/dotnet/framework/winforms/advanced/application-settings-for-windows-forms).

**Modyfikator dostępu**

Przycisk **modyfikator dostępu** określa poziom dostępu `Properties.Settings` (in C#) lub `My.Settings` (w Visual Basic) klasy pomocników, które program Visual Studio generuje w *Settings.Designer.cs* lub *Settings. Designer. vb*.

W przypadku C# projektów wizualnych modyfikator dostępu może być **wewnętrzny** lub **publiczny**.

W przypadku projektów Visual Basic modyfikator dostępu może być **zaprzyjaźniony** lub **publiczny**.

Domyślnie to ustawienie jest **wewnętrzne** C# i **zaprzyjaźnione** w Visual Basic. Gdy program Visual Studio generuje klasy pomocników jako **wewnętrzne** lub **zaprzyjaźnione**, pliki wykonywalne ( *. exe*) nie mogą uzyskać dostępu do zasobów i ustawień, które zostały dodane do biblioteki klas (pliki *. dll* ). Jeśli konieczne jest udostępnianie zasobów i ustawień z biblioteki klas, należy ustawić modyfikator dostępu na **Public**.

Aby uzyskać więcej informacji na temat klas pomocnika ustawień, zobacz [Zarządzanie ustawieniami aplikacji](../managing-application-settings-dotnet.md).

## <a name="settings-grid"></a>Siatka ustawień

**Siatka ustawień** służy do konfigurowania ustawień aplikacji. Ta siatka zawiera następujące kolumny:

**Nazwa**

Wprowadź nazwę ustawienia aplikacji w tym polu.

**Wprowadź**

Użyj listy rozwijanej, aby wybrać typ ustawienia. Najczęściej używane typy pojawiają się na liście rozwijanej, na przykład **ciąg**, **(ciąg połączenia)** i **System. Drawing. Font**. Możesz wybrać inny typ, wybierając pozycję **Przeglądaj** na końcu listy, a następnie wybierając typ z okna dialogowego **Wybierz typ** . Po wybraniu typu zostanie on dodany do typów wspólnych na liście rozwijanej (tylko dla bieżącego rozwiązania).

**Zakres**

Wybierz **aplikację** lub **użytkownika**.

Ustawienia zakresu aplikacji, takie jak parametry połączenia, są skojarzone z aplikacją. Użytkownicy nie mogą zmieniać ustawień o zakresie aplikacji w czasie wykonywania.

Ustawienia o zakresie użytkownika, takie jak czcionki systemowe, są przeznaczone do użycia w preferencjach użytkownika. Użytkownicy mogą je zmienić w czasie wykonywania.

**Wartość**

Dane lub wartość skojarzona z ustawieniem aplikacji. Na przykład, jeśli ustawienie jest czcionką, jej wartością może być **Verdana, 9.75 pt, style = Bold**.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie ustawieniami aplikacji](../managing-application-settings-dotnet.md)
- [Dostęp do ustawień aplikacji (Visual Basic)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)