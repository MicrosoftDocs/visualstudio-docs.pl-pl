---
title: Tworzenie aplikacji z natywnym interfejsem użytkownika przy użyciu platformy Xamarin
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: 30f137e6-595d-4ce7-b8f5-415b07c1caa2
caps.latest.revision: 33
ms.author: crdun
manager: crdun
ms.openlocfilehash: 7a0284ab6b8d2e89e1c0129c2bc98fb486918f90
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297919"
---
# <a name="build-apps-with-native-ui-using-xamarin-in-visual-studio"></a>Tworzenie aplikacji za pomocą natywnego interfejsu użytkownika przy użyciu platformy Xamarin w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po wykonaniu kroków opisanych w [instalatorze i zainstalowaniu](../cross-platform/setup-and-install.md) i [zweryfikowaniu środowiska Xamarin](../cross-platform/verify-your-xamarin-environment.md)w tym instruktażu pokazano, jak utworzyć podstawową aplikację platformy Xamarin (pokazaną poniżej) za pomocą natywnych warstw interfejsu użytkownika. Z natywnym interfejsem użytkownika udostępnionego kodu, który znajduje się w bibliotece klas przenośnych (PCL) i platform poszczególnych projektów zawierają definicje interfejsu użytkownika.

 ![Aplikacja platformy Xamarin w systemach Android i Windows Phone](../cross-platform/media/cross-plat-xamarin-build-1.png "Wielostronicowa kompilacja Xamarin 1")

 Wykonasz te czynności na tworzenie:

- [Konfigurowanie rozwiązania](#solution)

- [Zapisz kod usługi danych udostępnionych](#dataservice)

- [Projektowanie interfejsu użytkownika dla systemu Android](#Android)

- [Projektowanie interfejsu użytkownika dla Windows Phone](#Windows)

- [Następne kroki](#next)

> [!TIP]
> Pełny kod źródłowy tego projektu można znaleźć w [repozytorium Mobile-Samples w witrynie GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).
>
> Jeśli masz problemy lub występują błędy, Zaksięguj pytania w witrynie [forums.Xamarin.com](https://forums.xamarin.com/). Wiele błędów można rozwiązać przez aktualizację do najnowszych zestawów SDK wymaganych przez platformę Xamarin, które są opisane w [informacjach o wersji programu Xamarin](https://developer.xamarin.com/) dla każdej platformy.
>
> [!NOTE]
> Dokumentacja dla deweloperów platformy Xamarin oferuje również kilka przewodników z sekcjami Szybki Start i szczegółowe informacje wymienione poniżej. Na tych stronach upewnij się, że wybrano "Visual Studio", w prawym górnym rogu strony, aby wyświetlić wskazówki dotyczące programu Visual Studio.
>
> - Aplikacje platformy Xamarin z natywnym interfejsem użytkownika:
>
>   - [Witaj, Android](https://developer.xamarin.com/guides/android/getting_started/hello,android/) (prosta aplikacja z jednym ekranem)
>   - [Witaj, wieloekranu systemu Android](https://developer.xamarin.com/guides/android/getting_started/hello,android_multiscreen/) (aplikacja z nawigacją między ekranami)
>   - [Przewodnik po fragmentach systemu Android](https://docs.microsoft.com/xamarin/android/platform/fragments/implementing-with-fragments/) (używany w przypadku ekranów master/detail, między innymi)
>   - [Witaj, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
>   - [Witaj, iOS Multiscreen (wiele ekranów)](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS_multiscreen/)
>   - Aplikacje Xamarin przy użyciu zestawu narzędzi Xamarin.Forms (współdzielony interfejs użytkownika)
>
>   - [Witaj, Xamarin.Forms](https://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/hello-xamarin-forms/quickstart/)
>   - [Witaj, Xamarin.Forms (wiele ekranów)](https://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/hello-xamarin-forms-multiscreen/)

## <a name="solution"></a>Konfigurowanie rozwiązania
 Te kroki służą utworzeniu rozwiązania Xamarin za pomocą natywnego interfejsu użytkownika, który zawiera PCL dla udostępnionego kodu i dwa dodano pakiety NuGet.

1. W programie Visual Studio Utwórz nowe rozwiązanie **pusta aplikacja (natywna przenośna)** i nadaj mu nazwę **WeatherApp**. Ten szablon można łatwo znaleźć, wprowadzając **natywne przenośne** w polu wyszukiwania.

    Jeśli tak nie jest, może być konieczne zainstalowanie platformy Xamarin lub włączenie funkcji programu Visual Studio 2015, zobacz [Instalacja i instalacja](../cross-platform/setup-and-install.md).

2. Po kliknięciu przycisku OK spowoduje utworzenie rozwiązania, będziesz mieć wiele pojedynczych projektów:

   - **WeatherApp (przenośny)** : PCL, w której będziesz pisać kod, który jest współużytkowany na różnych platformach, w tym typowej logiki biznesowej i kodu interfejsu użytkownika przy użyciu programu Xamarin. Forms.

   - **WeatherApp. Droid**: projekt, który zawiera natywny kod systemu Android. To jest ustawiony jako domyślny projekt startowy.

   - **WeatherApp. iOS**: projekt zawierający natywny kod systemu iOS.

   - **WeatherApp. WinPhone (Windows Phone 8,1)** : projekt zawierający kod natywnej Windows Phone.

     W ramach każdego natywnego projektu mają dostęp do natywnych projektanta dla odpowiednich platform i zaimplementować platformy określonymi ekranami.

3. Dodaj pakiet **Newtonsoft. JSON** i NuGet do projektu PCL, który będzie używany do przetwarzania informacji pobranych z usługi danych pogody:

   - Kliknij prawym przyciskiem myszy **rozwiązanie "WeatherApp"** w Eksploratorze rozwiązań i wybierz pozycję **Zarządzaj pakietami NuGet dla rozwiązania.** ..

        W oknie NuGet wybierz kartę **Przeglądaj** i wyszukaj ciąg **Newtonsoft**.

   - Wybierz **Newtonsoft. JSON**.

   - Po prawej stronie okna Sprawdź projekt **WeatherApp** (jest to jedyny projekt, w którym należy zainstalować pakiet).

   - Upewnij się, że w polu **wersja** jest ustawiona **Najnowsza stabilna** wersja.

   - Kliknij polecenie **Zainstaluj**.

   - ![Lokalizowanie i instalowanie pakietu NuGet Newtonsoft. JSON](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")

4. Powtórz krok 3, aby znaleźć i zainstalować pakiet **Microsoft.NET. http** .

5. Skompiluj rozwiązanie i upewnij się, że żadne błędy kompilacji.

## <a name="dataservice"></a>Zapisz kod usługi danych udostępnionych
 Projekt **WeatherApp (przenośny)** polega na tym, że napiszesz kod dla biblioteki klas przenośnych (PCL), która jest udostępniana na wszystkich platformach. Pakiety aplikacji skompilowanymi z systemem iOS, Android i Windows Phone projektów jest automatycznie dołączany PCL.

 Poniższe kroki następnie dodać kod do aplikacji PCL dostęp do przechowywania danych pochodzących z tej usługi pogody:

1. Aby uruchomić ten przykład, należy najpierw zarejestrować się w celu uzyskania bezpłatnego klucza interfejsu API w [http://openweathermap.org/appid](https://openweathermap.org/appid).

2. Kliknij prawym przyciskiem myszy projekt **WeatherApp** i wybierz polecenie **Dodaj klasę >...** . W oknie dialogowym **Dodaj nowy element** nazwij plik **Weather.cs**. Ta klasa będzie używane do przechowywania danych z usługi danych o pogodzie.

3. Zastąp całą zawartość **Weather.cs** poniższymi:

    ```csharp
    namespace WeatherApp
    {
        public class Weather
        {
            public string Title { get; set; }
            public string Temperature { get; set; }
            public string Wind { get; set; }
            public string Humidity { get; set; }
            public string Visibility { get; set; }
            public string Sunrise { get; set; }
            public string Sunset { get; set; }

            public Weather()
            {
                //Because labels bind to these values, set them to an empty string to
                //ensure that the label appears on all platforms by default.
                this.Title = " ";
                this.Temperature = " ";
                this.Wind = " ";
                this.Humidity = " ";
                this.Visibility = " ";
                this.Sunrise = " ";
                this.Sunset = " ";
            }
        }
    }
    ```

4. Dodaj kolejną klasę do projektu PCL o nazwie **DataService.cs** , w którym będziesz używać do przetwarzania danych JSON z usługi danych pogody.

5. Zastąp całą zawartość **DataService.cs** następującym kodem:

    ```csharp
    using System.Threading.Tasks;
    using Newtonsoft.Json;
    using System.Net.Http;

    namespace WeatherApp
    {
        public class DataService
        {
            public static async Task<dynamic> getDataFromService(string queryString)
            {
                HttpClient client = new HttpClient();
                var response = await client.GetAsync(queryString);

                dynamic data = null;
                if (response != null)
                {
                    string json = response.Content.ReadAsStringAsync().Result;
                    data = JsonConvert.DeserializeObject(json);
                }

                return data;
            }
        }
    }
    ```

6. Dodaj trzecią klasę do pliku PCL o nazwie **Core** , w której umieścisz wspólną logikę biznesową, taką jak logika, która tworzy ciąg zapytania z kodem pocztowym, wywołuje usługę danych pogody i wypełnia wystąpienie klasy **Pogoda** .

7. Zastąp zawartość **Core.cs** poniższymi:

    ```csharp
    using System;
    using System.Threading.Tasks;

    namespace WeatherApp
    {
        public class Core
        {
            public static async Task<Weather> GetWeather(string zipCode)
            {
                //Sign up for a free API key at http://openweathermap.org/appid
                string key = "YOUR KEY HERE";
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="
                    + zipCode + ",us&appid=" + key + "&units=imperial";

                //Make sure developers running this sample replaced the API key
                if (key == "YOUR API KEY HERE")
                {
                    throw new ArgumentException("You must obtain an API key from openweathermap.org/appid and save it in the 'key' variable.");
                }

                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);

                if (results["weather"] != null)
                {
                    Weather weather = new Weather();
                    weather.Title = (string)results["name"];
                    weather.Temperature = (string)results["main"]["temp"] + " F";
                    weather.Wind = (string)results["wind"]["speed"] + " mph";
                    weather.Humidity = (string)results["main"]["humidity"] + " %";
                    weather.Visibility = (string)results["weather"][0]["main"];

                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);
                    weather.Sunrise = sunrise.ToString() + " UTC";
                    weather.Sunset = sunset.ToString() + " UTC";
                    return weather;
                }
                else
                {
                    return null;
                }
            }
        }
    }
    ```

8. Zastąp *klucz w tym miejscu* w kodzie interfejsem API uzyskanym w kroku 1 (nadal wymaga cudzysłowu).

9. Usuń MyClass.cs w aplikacji PCL, ponieważ firma Microsoft nie będzie go używać.

10. Skompiluj projekt **WeatherApp** PCL, aby upewnić się, że kod jest poprawny.

## <a name="Android"></a>Projektowanie interfejsu użytkownika dla systemu Android
 Teraz firma Microsoft będzie projektuje się interfejs użytkownika, połącz go ze współużytkowanym kodem, a następnie uruchom aplikację.

### <a name="design-the-look-and-feel-of-your-app"></a>Projektowanie wyglądu i działania aplikacji

1. W **Eksplorator rozwiązań**rozwiń folder **WeatherApp. Droid**>**zasoby**>**Układ** i Otwórz **Main. axml**. Spowoduje to otwarcie pliku projektanta wizualnego. (Jeśli pojawia się błąd związany z językiem Java, zobacz ten [wpis w blogu](https://forums.xamarin.com/discussion/32365/connection-to-the-layout-renderer-failed-in-xs-5-7-and-xamarinvs-3-9)).

    > [!TIP]
    > Istnieją inne pliki w projekcie. Eksplorowanie ich wykracza poza zakres tego tematu, ale jeśli chcesz szczegółowe do struktury projektu systemu Android nieco więcej, zobacz [część 2 głębokie szczegółowe](https://docs.microsoft.com/xamarin/android/get-started/hello-android/hello-android-deepdive?pivots=windows) tematu Hello Android w witrynie Xamarin.com.

2. Wybierz i usuń przycisk domyślny, który pojawia się w projektancie.

3. Otwórz przybornik z **widokiem > innym przyborniku > systemu Windows**.

4. Z **przybornika**przeciągnij kontrolkę **RelativeLayout** na projektanta. Użyjesz tego formantu jako kontenera nadrzędnego dla innych kontrolek.

    > [!TIP]
    > Jeśli w dowolnym momencie układ nie będzie wyświetlany prawidłowo, Zapisz plik i przełączenie między kartami **projekt** i **Źródło** , aby odświeżyć.

5. W oknie **Właściwości** ustaw właściwość **Background** (w grupie stylów) na `#545454`.

6. Z **przybornika**przeciągnij formant **TextView** do kontrolki **RelativeLayout** .

7. W oknie **Właściwości** ustaw następujące właściwości (Uwaga: może pomóc posortować listę alfabetycznie przy użyciu przycisku sortowania na pasku narzędzi okno właściwości):

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Opis**|**Wyszukaj według kodu pocztowego**|
    |**id**|`@+id/ZipCodeSearchLabel`|
    |**layout_marginLeft**|`10dp`|
    |**textColor**|`@android:color/white`|
    |**System utworzył czcionkę**|`bold`|

    > [!TIP]
    > Należy zauważyć, że wiele właściwości nie zawierają listy rozwijanej wartości, które można wybrać.  Może być trudne do odgadnięcia, jaka wartość ciągu dla dowolnej podanej właściwości. W przypadku sugestii spróbuj wyszukać nazwę właściwości na stronie klasy [R. ATTR](https://developer.android.com/reference/android/R.attr.html) .
    >
    >  Ponadto szybkie wyszukiwanie w Internecie często prowadzi do strony na [http://stackoverflow.com/](https://stackoverflow.com/) , gdzie inne osoby używały tej samej właściwości.

     Aby uzyskać odwołanie, po przełączeniu do widoku **źródła** , w przypadku tego elementu powinien zostać wyświetlony następujący kod:

    ```xml
    <TextView
        android:text="Search by Zip Code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/ZipCodeSearchLabel"
        android:layout_centerVertical="true"
        android:layout_marginLeft="10dp"
        android:textColor="@android:color/white"
        android:textStyle="bold" />

    ```

8. Z **przybornika**przeciągnij kontrolkę **TextView** na kontrolkę **RelativeLayout** i umieść ją pod kontrolką ZipCodeSearchLabel. Można to zrobić, porzucenie nowej kontrolki na odpowiednią krawędzią istniejącej kontrolki; pomaga ono powiększenia projektanta w pewnym stopniu, w tym.

9. W oknie **Właściwości** ustaw następujące właściwości:

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Opis**|**Kod pocztowy**|
    |**id**|`@+id/ZipCodeLabel`|
    |**layout_marginLeft**|`10dp`|
    |**layout_marginTop**|`5dp`|

     Kod w widoku **źródła** powinien wyglądać następująco:

    ```xml
    <TextView
        android:text="Zip Code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/ZipCodeSearchLabel"
        android:id="@+id/ZipCodeLabel"
        android:layout_marginTop="5dp"
        android:layout_marginLeft="10dp" />
    ```

10. Z **przybornika**przeciągnij kontrolkę **Number** na **RelativeLayout**, umieść ją pod etykietą **kodu pocztowego** . Następnie ustaw następujące właściwości:

    |Właściwość|Wartość|
    |--------------|-----------|
    |**id**|`@+id/zipCodeEntry`|
    |**layout_marginLeft**|`10dp`|
    |**layout_marginBottom**|`10dp`|
    |**Szerokość**|`165dp`|

     Ponownie kod:

    ```xml
    <EditText
        android:inputType="number"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/ZipCodeLabel"
        android:id="@+id/zipCodeEntry"
        android:layout_marginLeft="10dp"
        android:layout_marginBottom="10dp"
        android:width="165dp" />
    ```

11. Z **przybornika**przeciągnij **przycisk** na kontrolkę **RelativeLayout** i umieść go po prawej stronie kontrolki zipCodeEntry. Następnie ustaw następujące właściwości:

    |Właściwość|Wartość|
    |--------------|-----------|
    |**id**|`@+id/weatherBtn`|
    |**Opis**|**Uzyskaj Pogoda**|
    |**layout_marginLeft**|`20dp`|
    |**layout_alignBottom**|`@id/zipCodeEntry`|
    |**Szerokość**|`165dp`|

    ```xml
    <Button    android:text="Get Weather"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_toRightOf="@id/zipCodeEntry"
        android:id="@+id/weatherBtn"
        android:layout_marginLeft="20dp"
        android:layout_alignBottom="@id/zipCodeEntry"
        android:width="165dp" />
    ```

12. Teraz masz wystarczająco dużo środowisko, aby utworzyć podstawowy interfejs użytkownika przy użyciu narzędzia Android designer. Można także utworzyć interfejs użytkownika, dodając znaczników bezpośrednio do pliku .asxml strony. Aby skompilować resztę interfejsu użytkownika w ten sposób, przełącz się do widoku źródła w projektancie, a następnie Poniższa etykieta *poniżej tagu* `</RelativeLayout>` (tak, jest poniżej tagu... te elementy nie są zawarte w ReleativeLayout).

    ```xml
    <TextView
            android:text="Location"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/locationLabel"
            android:layout_marginLeft="10dp"
            android:layout_marginTop="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/locationText"
            android:layout_marginLeft="20dp"
            android:layout_marginBottom="10dp" />
        <TextView
            android:text="Temperature"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/tempLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/tempText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Wind Speed"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/windLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/windText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Humidity"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/humidtyLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/humidityText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Visibility"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/visibilityLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/visibilityText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Time of Sunrise"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunriseLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunriseText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Time of Sunset"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunsetLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunsetText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />

    ```

13. Zapisz plik i Przełącz się do widoku **projektu** . Interfejs użytkownika powinien wyglądać w następujący sposób:

     ![Interfejs użytkownika dla aplikacji systemu Android](../cross-platform/media/xamarin-androidui.png "Xamarin_AndroidUI")

14. Otwórz **MainActivity.cs** i Usuń wiersze z metody *OnCreate* , które odwołują się do przycisku domyślnego, który został usunięty wcześniej. Kod powinien wyglądać następująco po wykonaniu tych czynności:

    ```
    protected override void OnCreate (Bundle bundle)
    {
        base.OnCreate (bundle);

        // Set our view from the "main" layout resource
        SetContentView (Resource.Layout.Main);
    }
    ```

15. Skompiluj projekt dla systemu Android, aby sprawdzić swoją pracę. Należy zauważyć, że kompilacja dodaje identyfikatory kontroli do pliku **Resource.Designer.cs** , dzięki czemu można odwoływać się do kontrolek według nazwy w kodzie.

### <a name="consume-your-shared-code"></a>Korzystanie ze współużytkowanym kodem

1. Otwórz plik **MainActivity.cs** projektu **WeatherApp** w edytorze kodu i Zastąp jego zawartość następującym kodem. Ten kod wywołuje metodę `GetWeather`, która została zdefiniowana w kodzie udostępnionym. Następnie w interfejsie użytkownika aplikacji zawiera dane, które są pobierane z tej metody.

    ```csharp
    using System;
    using Android.App;
    using Android.Widget;
    using Android.OS;

    namespace WeatherApp.Droid
    {
        [Activity(Label = "Sample Weather App", MainLauncher = true, Icon = "@drawable/icon")]
        public class MainActivity : Activity
        {
            protected override void OnCreate(Bundle bundle)
            {
                base.OnCreate(bundle);

                SetContentView(Resource.Layout.Main);

                Button button = FindViewById<Button>(Resource.Id.weatherBtn);

                button.Click += Button_Click;
            }

            private async void Button_Click(object sender, EventArgs e)
            {
                EditText zipCodeEntry = FindViewById<EditText>(Resource.Id.zipCodeEntry);

                if (!String.IsNullOrEmpty(zipCodeEntry.Text))
                {
                    Weather weather = await Core.GetWeather(zipCodeEntry.Text);
                    FindViewById<TextView>(Resource.Id.locationText).Text = weather.Title;
                    FindViewById<TextView>(Resource.Id.tempText).Text = weather.Temperature;
                    FindViewById<TextView>(Resource.Id.windText).Text = weather.Wind;
                    FindViewById<TextView>(Resource.Id.visibilityText).Text = weather.Visibility;
                    FindViewById<TextView>(Resource.Id.humidityText).Text = weather.Humidity;
                    FindViewById<TextView>(Resource.Id.sunriseText).Text = weather.Sunrise;
                    FindViewById<TextView>(Resource.Id.sunsetText).Text = weather.Sunset;
                }
            }
        }
    }
    ```

### <a name="run-the-app-and-see-how-it-looks"></a>Uruchom aplikację i zobaczyć, jak wygląda

1. W **Eksplorator rozwiązań**upewnij się, że projekt **WeatherApp. Droid** jest ustawiony jako projekt startowy.

2. Wybierz odpowiednie urządzenie lub emulator docelowego, a następnie uruchom aplikację, naciskając klawisz F5.

3. Na urządzeniu lub w emulatorze wpisz prawidłowy kod pocztowy Stany Zjednoczone w polu edycji (na przykład: 60601) i naciśnij pozycję **Pobierz Pogoda**. Dane o pogodzie dla tego regionu pojawi się w kontrolkach.

     ![Aplikacja pogody dla systemów Android i Windows Phone](../cross-platform/media/xamarin-getstarted-results.png "Xamarin_GetStarted_Results")

> [!TIP]
> Pełny kod źródłowy tego projektu znajduje się w [repozytorium Mobile-Samples w witrynie GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).

## <a name="Windows"></a>Projektowanie interfejsu użytkownika dla Windows Phone
 Teraz firma Microsoft będzie projektowania interfejsu użytkownika programu Windows Phone, połącz go ze współużytkowanym kodem, a następnie uruchom aplikację.

### <a name="design-the-look-and-feel-of-your-app"></a>Projektowanie wyglądu i działania aplikacji
 Proces projektowania natywnego interfejsu użytkownika Windows Phone w aplikacji platformy Xamarin nie różni się od innych natywnej aplikacji Windows Phone. Z tego powodu firma Microsoft nie będzie przejdź do szczegółów, w tym miejscu w sposób używania projektanta. W tym celu zapoznaj się z tematem [Tworzenie interfejsu użytkownika przy użyciu Projektant XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

 Zamiast tego po prostu otwórz plik MainPage.xaml i Zastąp cały kod XAML następujących czynności:

```xaml
<Page
    x:Class="WeatherApp.WinPhone.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:WeatherApp.WinPhone"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">

    <Grid>
        <StackPanel HorizontalAlignment="Left" Height="40" Margin="10,0,0,0" VerticalAlignment="Top" Width="400">
            <TextBlock x:Name="pageTitle" Text="Weather App" FontSize="30" />
        </StackPanel>
        <StackPanel HorizontalAlignment="Left" Height="120" Margin="10,40,0,0" VerticalAlignment="Top" Width="400" Background="#FF545454">

            <TextBlock x:Name="zipCodeSearchLabel" TextWrapping="Wrap" Text="Search by Zip Code" FontSize="18" FontWeight="Bold" HorizontalAlignment="Left" Margin="10,10,0,0"/>
            <TextBlock x:Name="zipCodeLabel" TextWrapping="Wrap" Text="Zip Code" Margin="10,5,0,0" FontSize="14" Foreground="#FFA8A8A8"/>
            <StackPanel Orientation="Horizontal">
                <TextBox x:Name="zipCodeEntry" Margin="10,10,0,0" Text="" VerticalAlignment="Top" InputScope="Number" Width="165" />
                <Button x:Name="weatherBtn" Content="Get Weather" Width="165" Margin="20,0,0,0" Height="60" Click="GetWeatherButton_Click"/>
            </StackPanel>
        </StackPanel>
        <StackPanel Margin="10,175,0,0">
            <TextBlock x:Name="locationLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Location" VerticalAlignment="Top"/>
            <TextBlock x:Name="locationText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="tempLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Temperature" VerticalAlignment="Top"/>
            <TextBlock x:Name="tempText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="windLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Wind Speed" VerticalAlignment="Top"/>
            <TextBlock x:Name="windText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="humidityLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Humidity" VerticalAlignment="Top"/>
            <TextBlock x:Name="humidityText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="visibilityLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Temperature" VerticalAlignment="Top"/>
            <TextBlock x:Name="visibilityText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunriseLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Time of Sunriweatherse" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunriseText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunsetLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Time of Sunset" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunsetText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
        </StackPanel>
    </Grid>
</Page>
```

 W widoku Projekt interfejs użytkownika powinien wyglądać w następujący sposób:

 ![Interfejs użytkownika aplikacji Windows Phone](../cross-platform/media/xamarin-winphone-finalui.png "Xamarin_WinPhone_FinalUI")

### <a name="consume-your-shared-code"></a>Korzystanie ze współużytkowanym kodem

1. W Projektancie wybierz przycisk **Pobierz Pogoda** .

2. W oknie **Właściwości** wybierz przycisk programu obsługi zdarzeń (ikona obsługi![zdarzeń programu Visual Studio](../cross-platform/media/blend-vs-eventhandlers-icon.png "blend_VS_EventHandlers_icon")).

     Ta ikona jest wyświetlana w górnym rogu okna **Właściwości** .

3. Obok zdarzenia **kliknięcia** wpisz **GetWeatherButton_Click**, a następnie naciśnij klawisz ENTER.

     Spowoduje to wygenerowanie procedury obsługi zdarzeń o nazwie `GetWeatherButton_Click`. Edytor kodu otwiera się i umieszcza kursor wewnątrz bloku kodu programu obsługi zdarzeń.  Uwaga: Jeśli nie zostanie otwarta po naciśnięciu klawisza ENTER edytorze, po prostu dwukrotnie kliknąć nazwę zdarzenia.

4. Zastąp ten program obsługi zdarzeń z następującym kodem.

    ```csharp
    private async void GetWeatherButton_Click(object sender, RoutedEventArgs e)
    {
        if (!String.IsNullOrEmpty(zipCodeEntry.Text))
        {
            Weather weather = await Core.GetWeather(zipCodeEntry.Text);
            locationText.Text = weather.Title;
            tempText.Text = weather.Temperature;
            windText.Text = weather.Wind;
            visibilityText.Text = weather.Visibility;
            humidityText.Text = weather.Humidity;
            sunriseText.Text = weather.Sunrise;
            sunsetText.Text = weather.Sunset;

            weatherBtn.Content = "Search Again";
        }
    }
    ```

     Ten kod wywołuje metodę `GetWeather`, która została zdefiniowana w kodzie udostępnionym. Jest to tę samą metodę, która wywołana w aplikacji systemu Android. Ten kod zawiera również dane pobrane z tej metody w kontrolek interfejsu użytkownika aplikacji.

5. W MainPage.xaml.cs, który jest otwarty, usuń cały kod wewnątrz metody **OnNavigatedTo** . Ten kod po prostu obsługiwane przycisk domyślny, która została usunięta, gdy zastąpiliśmy zawartość pliku MainPage.xaml.

### <a name="run-the-app-and-see-how-it-looks"></a>Uruchom aplikację i zobaczyć, jak wygląda

1. W **Eksplorator rozwiązań**Ustaw projekt **WeatherApp. WinPhone** jako projekt startowy.

2. Uruchom aplikację, naciskając klawisz F5.

3. W emulatorze Windows Phone wpisz prawidłowy Stany Zjednoczone Kod pocztowy w polu edycji (na przykład: 60601) i naciśnij pozycję **Pobierz Pogoda**. Dane o pogodzie dla tego regionu pojawi się w kontrolkach.

     ![Wersja systemu Windows działającej aplikacji](../cross-platform/media/xamarin-getstarted-results-windows.png "Xamarin_GetStarted_Results_Windows")

> [!TIP]
> Pełny kod źródłowy tego projektu znajduje się w [repozytorium Mobile-Samples w witrynie GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).

## <a name="next"></a> Następne kroki
 **Dodawanie interfejsu użytkownika dla systemu iOS do rozwiązania**

 W tym przykładzie należy rozszerzyć przez dodanie natywnego interfejsu użytkownika dla systemu iOS. W tym należy połączyć się z komputerem Mac w sieci lokalnej, która ma Xcode i Xamarin zainstalowane. Po wykonaniu tej czynności można użyć narzędzia iOS designer bezpośrednio w programie Visual Studio. Zapoznaj się z [repozytorium Mobile-Samples w witrynie GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather) , aby uzyskać ukończoną aplikację.

 Zapoznaj się również z przewodnikiem [Hello, iOS](https://docs.microsoft.com/xamarin/ios/get-started/hello-ios/hello-ios-quickstart?pivots=windows) (Xamarin.com). Należy zauważyć, że na tej stronie można się, że "Visual Studio" jest zaznaczona w w prawym górnym rogu strony na strony xamarin.com i poprawny zestaw instrukcji.

 **Dodawanie kodu specyficznego dla platformy w projekcie udostępnionym**

 Udostępnionego kodu w aplikacji PCL jest niezależny od platformy, ponieważ kompilacji raz i zawarte w każdy pakiet specyficzne dla platformy aplikacji PCL. Jeśli chcesz napisać współużytkowany kod, który używa kompilacji warunkowej do izolowania kodu specyficznego dla platformy, możesz użyć projektu *udostępnionego* . Aby uzyskać więcej informacji, zobacz [Opcje udostępniania Node](https://docs.microsoft.com/xamarin/cross-platform/app-fundamentals/code-sharing) (Xamarin.com).

## <a name="see-also"></a>Zobacz też
 [Witryna Xamarin Developer site](https://docs.microsoft.com/xamarin/) [Windows Dev Center](https://dev.windows.com/en-us) [— C# informacje o skrócie i szybkim plakatie](https://aka.ms/scposter)
