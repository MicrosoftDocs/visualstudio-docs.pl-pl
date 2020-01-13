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
ms.openlocfilehash: 204d3ee68aace07ed19e5913309a122d6d775a0e
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918347"
---
# <a name="build-apps-with-native-ui-using-xamarin-in-visual-studio"></a>Tworzenie aplikacji za pomocą natywnego interfejsu użytkownika przy użyciu platformy Xamarin w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po wykonaniu kroków [Instalator i instalacja](../cross-platform/setup-and-install.md) i [Sprawdź swoje środowisko Xamarin](../cross-platform/verify-your-xamarin-environment.md), w tym instruktażu dowiesz się, jak utworzyć podstawową aplikację platformy Xamarin (pokazana poniżej), za pomocą natywnego warstwy interfejsu użytkownika. Z natywnym interfejsem użytkownika udostępnionego kodu, który znajduje się w bibliotece klas przenośnych (PCL) i platform poszczególnych projektów zawierają definicje interfejsu użytkownika.

 ![Aplikacja platformy Xamarin w systemach Android i Windows Phone](../cross-platform/media/cross-plat-xamarin-build-1.png "Wielostronicowa kompilacja Xamarin 1")

 Wykonasz te czynności na tworzenie:

- [Konfigurowanie rozwiązania programu](#solution)

- [Pisanie kodu usług udostępnionych danych](#dataservice)

- [Projektowanie interfejsu użytkownika dla systemu Android](#Android)

- [Projekt interfejsu użytkownika programu Windows Phone](#Windows)

- [Następne kroki](#next)

> [!TIP]
> Możesz znaleźć pełnego kodu źródłowego dla tego projektu w [mobile-samples repository w witrynie GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).
>
> Jeśli masz trudności lub występują błędy, Opublikuj pytania na [forums.xamarin.com](https://forums.xamarin.com/). Wiele błędów, które można rozwiązać, aktualizując do najnowsze zestawy SDK wymagane przez środowisko Xamarin, które są opisane w [informacje o wersji platformy Xamarin](https://developer.xamarin.com/) dla każdej platformy.
>
> [!NOTE]
> Dokumentacja dla deweloperów platformy Xamarin oferuje również kilka przewodników z sekcjami Szybki Start i szczegółowe informacje wymienione poniżej. Na tych stronach upewnij się, że wybrano "Visual Studio", w prawym górnym rogu strony, aby wyświetlić wskazówki dotyczące programu Visual Studio.
>
> - Aplikacje platformy Xamarin z natywnym interfejsem użytkownika:
>
>   - [Witaj, Android](https://developer.xamarin.com/guides/android/getting_started/hello,android/) (prosta aplikacja z jednym ekranem)
>   - [Witaj, Android (wiele ekranów)](https://developer.xamarin.com/guides/android/getting_started/hello,android_multiscreen/) (aplikacja z nawigacją między ekranami)
>   - [Dla systemu android przewodnik fragmenty](/xamarin/android/platform/fragments/implementing-with-fragments/) (używane dla rekordu głównego/szczegółów ekranów, między innymi)
>   - [Witaj, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
>   - [Witaj, iOS Multiscreen (wiele ekranów)](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS_multiscreen/)
>   - Aplikacje Xamarin przy użyciu zestawu narzędzi Xamarin.Forms (współdzielony interfejs użytkownika)
>
>   - [Witaj, Xamarin.Forms](https://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/hello-xamarin-forms/quickstart/)
>   - [Witaj, Xamarin.Forms (wiele ekranów)](https://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/hello-xamarin-forms-multiscreen/)

## <a name="solution"></a> Konfigurowanie rozwiązania programu
 Te kroki służą utworzeniu rozwiązania Xamarin za pomocą natywnego interfejsu użytkownika, który zawiera PCL dla udostępnionego kodu i dwa dodano pakiety NuGet.

1. W programie Visual Studio Utwórz nowy **pusta aplikacja (natywny przenośny)** rozwiązania i nadaj mu nazwę **WeatherApp**. Można znaleźć ten szablon najłatwiej, wprowadzając **przenośnego macierzystego** w polu wyszukiwania.

    Jeśli tak nie jest dostępne, może być konieczne instalacji Xamarin lub włączyć funkcję Visual Studio 2015, zobacz [Instalator i instalacja](../cross-platform/setup-and-install.md).

2. Po kliknięciu przycisku OK spowoduje utworzenie rozwiązania, będziesz mieć wiele pojedynczych projektów:

   - **WeatherApp (przenośna)** : PCL, gdzie Ty napiszesz kod, który jest współużytkowany przez platform, w tym wspólnej logiki biznesowej i kodu interfejsu użytkownika przy użyciu zestawu narzędzi Xamarin.Forms.

   - **WeatherApp.Droid**: projekt, który zawiera natywnego kodu dla systemu Android. To jest ustawiony jako domyślny projekt startowy.

   - **WeatherApp.iOS**: projekt, który zawiera kod natywny dla systemu iOS.

   - **WeatherApp.WinPhone (Windows Phone 8.1)** : projekt, który zawiera kod macierzysty Windows Phone.

     W ramach każdego natywnego projektu mają dostęp do natywnych projektanta dla odpowiednich platform i zaimplementować platformy określonymi ekranami.

3. Dodaj **Newtonsoft.Json** i pakiet NuGet do projektu PCL, którego będziesz używać do przetwarzania informacji pobrane z usługi danych o pogodzie:

   - Kliknij prawym przyciskiem myszy **rozwiązania "WeatherApp"** w Eksploratorze rozwiązań i wybierz pozycję **Zarządzaj pakietami NuGet dla rozwiązania...** .

        W oknie NuGet wybierz **Przeglądaj** kartę i wyszukaj **Newtonsoft**.

   - Wybierz **Newtonsoft.Json**.

   - Po prawej stronie okna, sprawdź **WeatherApp** projektu (jest to tylko projektu, w którym należy zainstalować pakiet).

   - Upewnij się, **wersji** pole jest ustawione na **najnowszy stabilny** wersji.

   - Kliknij przycisk **zainstalować**.

   - ![Lokalizowanie i instalowanie pakietu NuGet Newtonsoft. JSON](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")

4. Powtórz kroki od 3, aby znaleźć i zainstalować **Microsoft.Net.Http** pakietu.

5. Skompiluj rozwiązanie i upewnij się, że żadne błędy kompilacji.

## <a name="dataservice"></a> Pisanie kodu usług udostępnionych danych
 **WeatherApp (przenośna)** projekt jest, gdzie Ty napiszesz kod dla biblioteki klas przenośnych (PCL), który jest udostępniany na wszystkich platformach. Pakiety aplikacji skompilowanymi z systemem iOS, Android i Windows Phone projektów jest automatycznie dołączany PCL.

 Poniższe kroki następnie dodać kod do aplikacji PCL dostęp do przechowywania danych pochodzących z tej usługi pogody:

1. Aby uruchomić ten przykład, najpierw musisz zarejestrować się uzyskać bezpłatny klucz interfejsu API w [ http://openweathermap.org/appid ](https://openweathermap.org/appid).

2. Kliknij prawym przyciskiem myszy **WeatherApp** projektu, a następnie wybierz **Dodaj > klasa...** . W **Dodaj nowy element** okno dialogowe, nazwij plik **Weather.cs**. Ta klasa będzie używane do przechowywania danych z usługi danych o pogodzie.

3. Zastąp całą zawartość **Weather.cs** następującym kodem:

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

4. Dodaj klasę do projektu PCL o nazwie **DataService.cs** , w którym będziesz używać do przetwarzania danych JSON z usługi danych o pogodzie.

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

6. Dodaj klasę innych do PCL o nazwie **Core** którym zostanie umieszczony udostępnione logiki biznesowej, takich jak logiki, który wchodzi w skład ciąg zapytania z kod pocztowy, wywołuje usługę danych o pogodzie i wypełnia wystąpienie **pogody**klasy.

7. Zastąp zawartość **Core.cs** następującym kodem:

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

8. Zastąp *SWÓJ klucz tutaj* w kodzie za pomocą klucza interfejsu API, uzyskaną w kroku 1 (nadal wymaga ją w cudzysłowie).

9. Usuń MyClass.cs w aplikacji PCL, ponieważ firma Microsoft nie będzie go używać.

10. Tworzenie **WeatherApp** projektu PCL, aby upewnić się, kod jest poprawny.

## <a name="Android"></a> Projektowanie interfejsu użytkownika dla systemu Android
 Teraz firma Microsoft będzie projektuje się interfejs użytkownika, połącz go ze współużytkowanym kodem, a następnie uruchom aplikację.

### <a name="design-the-look-and-feel-of-your-app"></a>Projektowanie wyglądu i działania aplikacji

1. W **Eksploratora rozwiązań**, rozwiń węzeł **WeatherApp.Droid**>**zasobów**>**układ** folder i Otwórz **Main.axml**. Spowoduje to otwarcie pliku projektanta wizualnego. (Jeśli pojawi się błąd, który języka Java, zobacz ten [wpis w blogu](https://forums.xamarin.com/discussion/32365/connection-to-the-layout-renderer-failed-in-xs-5-7-and-xamarinvs-3-9).)

    > [!TIP]
    > Istnieją inne pliki w projekcie. Eksplorowanie ich jest poza zakresem tego tematu, ale jeśli chcesz od razu do struktury projektu dla systemu Android nieco więcej, zobacz [część 2 Deep Dive](/xamarin/android/get-started/hello-android/hello-android-deepdive?pivots=windows) Hello Android tematu na strony xamarin.com.

2. Wybierz i usuń przycisk domyślny, który pojawia się w projektancie.

3. Otwórz przybornika **Widok > inne Windows > przybornika**.

4. Z **przybornika**, przeciągnij **RelativeLayout** formant do projektanta. Użyjesz tego formantu jako kontenera nadrzędnego dla innych kontrolek.

    > [!TIP]
    > Jeśli w dowolnym momencie układ wydają się do poprawnego wyświetlania, Zapisz plik i przełączania się między **projektowania** i **źródła** kart, aby odświeżyć.

5. W **właściwości** oknie **tła** właściwości (w grupie Style) `#545454`.

6. Z **przybornika**, przeciągnij **TextView** kontrolować na **RelativeLayout** kontroli.

7. W **właściwości** okna ustawiania tych właściwości (Uwaga: może pomóc sortować listę alfabetycznie przy użyciu przycisku Sortuj na pasku narzędzi w oknie właściwości):

    |Właściwość|Wartość|
    |--------------|-----------|
    |**text**|**Wyszukaj według kod pocztowy**|
    |**id**|`@+id/ZipCodeSearchLabel`|
    |**layout_marginLeft**|`10dp`|
    |**textColor**|`@android:color/white`|
    |**textStyle**|`bold`|

    > [!TIP]
    > Należy zauważyć, że wiele właściwości nie zawierają listy rozwijanej wartości, które można wybrać.  Może być trudne do odgadnięcia, jaka wartość ciągu dla dowolnej podanej właściwości. Masz sugestie, spróbuj wyszukać nazwę właściwości w [R.attr](https://developer.android.com/reference/android/R.attr.html) klasy strony.
    >
    >  Ponadto wyszukiwania w sieci web szybkiego często prowadzi do strony [ http://stackoverflow.com/ ](https://stackoverflow.com/) inne osoby mają użycia tej samej właściwości.

     Odwołanie, jeśli zaczniesz **źródła** widoku, powinien zostać wyświetlony następujący kod dla tego elementu:

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

8. Z **przybornika**, przeciągnij **TextView** kontrolować na **RelativeLayout** kontroli i umieść ją poniżej kontrolki ZipCodeSearchLabel. Można to zrobić, porzucenie nowej kontrolki na odpowiednią krawędzią istniejącej kontrolki; pomaga ono powiększenia projektanta w pewnym stopniu, w tym.

9. W **właściwości** okna ustawiania tych właściwości:

    |Właściwość|Wartość|
    |--------------|-----------|
    |**text**|**Kod pocztowy**|
    |**id**|`@+id/ZipCodeLabel`|
    |**layout_marginLeft**|`10dp`|
    |**layout_marginTop**|`5dp`|

     Kod w **źródła** widok powinien wyglądać następująco:

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

10. Z **przybornika**, przeciągnij **numer** kontrolować na **RelativeLayout**, umieść ją poniżej **kod pocztowy** etykiety. Następnie ustaw następujące właściwości:

    |Właściwość|Wartość|
    |--------------|-----------|
    |**id**|`@+id/zipCodeEntry`|
    |**layout_marginLeft**|`10dp`|
    |**layout_marginBottom**|`10dp`|
    |**width**|`165dp`|

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

11. Z **przybornika**, przeciągnij **przycisk** na **RelativeLayout** kontroli i umieść ją po prawej stronie formantu zipCodeEntry. Następnie ustaw następujące właściwości:

    |Właściwość|Wartość|
    |--------------|-----------|
    |**id**|`@+id/weatherBtn`|
    |**text**|**Pobierz pogodę**|
    |**layout_marginLeft**|`20dp`|
    |**layout_alignBottom**|`@id/zipCodeEntry`|
    |**width**|`165dp`|

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

12. Teraz masz wystarczająco dużo środowisko, aby utworzyć podstawowy interfejs użytkownika przy użyciu narzędzia Android designer. Można także utworzyć interfejs użytkownika, dodając znaczników bezpośrednio do pliku .asxml strony. Aby utworzyć pozostałą część interfejsu użytkownika w ten sposób, przejdź do widoku źródła w projektancie, a następnie po niej następujące znaczniki *pod* `</RelativeLayout>` tag (tak, to poniżej tagu... te elementy nie są zawarte w ReleativeLayout).

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

13. Zapisz plik i przejdź do **projektowania** widoku. Interfejs użytkownika powinien wyglądać w następujący sposób:

     ![Interfejs użytkownika dla aplikacji systemu Android](../cross-platform/media/xamarin-androidui.png "Xamarin_AndroidUI")

14. Otwórz **MainActivity.cs** i usuwania wierszy w *OnCreate* metody odwołujące się do domyślnego przycisku, który został wcześniej usunięty. Kod powinien wyglądać następująco po wykonaniu tych czynności:

    ```
    protected override void OnCreate (Bundle bundle)
    {
        base.OnCreate (bundle);

        // Set our view from the "main" layout resource
        SetContentView (Resource.Layout.Main);
    }
    ```

15. Skompiluj projekt dla systemu Android, aby sprawdzić swoją pracę. Należy zauważyć, że tworzenie dodaje kontrolować identyfikatorów **Resource.Designer.cs** plików mogą odwoływać się do formantów według nazwy w kodzie.

### <a name="consume-your-shared-code"></a>Korzystanie ze współużytkowanym kodem

1. Otwórz **MainActivity.cs** pliku **WeatherApp** projektu w edytorze kodu, a następnie zastąp zawartość tego pliku poniższy kod. Ten kod wywołuje `GetWeather` metodę, która jest zdefiniowana w kodzie udostępnionych. Następnie w interfejsie użytkownika aplikacji zawiera dane, które są pobierane z tej metody.

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

1. W **Eksploratora rozwiązań**, upewnij się, że **WeatherApp.Droid** projekt jest ustawiony jako projekt startowy.

2. Wybierz odpowiednie urządzenie lub emulator docelowego, a następnie uruchom aplikację, naciskając klawisz F5.

3. Na urządzeniu lub w emulatorze wpisz poprawny kod pocztowy Stanów Zjednoczonych, w polu edycji (na przykład: 60601) i naciśnij klawisz **uzyskać pogody**. Dane o pogodzie dla tego regionu pojawi się w kontrolkach.

     ![Aplikacja pogody dla systemów Android i Windows Phone](../cross-platform/media/xamarin-getstarted-results.png "Xamarin_GetStarted_Results")

> [!TIP]
> Trwa pełnego kodu źródłowego dla tego projektu [mobile-samples repository w witrynie GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).

## <a name="Windows"></a> Projekt interfejsu użytkownika programu Windows Phone
 Teraz firma Microsoft będzie projektowania interfejsu użytkownika programu Windows Phone, połącz go ze współużytkowanym kodem, a następnie uruchom aplikację.

### <a name="design-the-look-and-feel-of-your-app"></a>Projektowanie wyglądu i działania aplikacji
 Proces projektowania natywnego interfejsu użytkownika Windows Phone w aplikacji platformy Xamarin nie różni się od innych natywnej aplikacji Windows Phone. Z tego powodu firma Microsoft nie będzie przejdź do szczegółów, w tym miejscu w sposób używania projektanta. Można znaleźć [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

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

1. W Projektancie zaznacz **uzyskać pogody** przycisku.

2. W oknie **Właściwości** wybierz przycisk programu obsługi zdarzeń (ikona obsługi![zdarzeń programu Visual Studio](../cross-platform/media/blend-vs-eventhandlers-icon.png "blend_VS_EventHandlers_icon")).

     Ikona ta pojawia się w górnym rogu **właściwości** okna.

3. Obok pozycji **kliknij** zdarzeń, typ **GetWeatherButton_Click**, a następnie naciśnij klawisz ENTER.

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

     Ten kod wywołuje `GetWeather` metodę, która jest zdefiniowana w kodzie udostępnionych. Jest to tę samą metodę, która wywołana w aplikacji systemu Android. Ten kod zawiera również dane pobrane z tej metody w kontrolek interfejsu użytkownika aplikacji.

5. W pliku MainPage.xaml.cs jest otwarty, usuń cały kod wewnątrz **OnNavigatedTo** metody. Ten kod po prostu obsługiwane przycisk domyślny, która została usunięta, gdy zastąpiliśmy zawartość pliku MainPage.xaml.

### <a name="run-the-app-and-see-how-it-looks"></a>Uruchom aplikację i zobaczyć, jak wygląda

1. W **Eksploratora rozwiązań**ustaw **WeatherApp.WinPhone** projekt jako projekt startowy.

2. Uruchom aplikację, naciskając klawisz F5.

3. Windows Phone, w emulatorze wpisz prawidłowy kod pocztowy w Stanach Zjednoczonych, w polu edycji (na przykład: 60601) i naciśnij klawisz **uzyskać pogody**. Dane o pogodzie dla tego regionu pojawi się w kontrolkach.

     ![Wersja systemu Windows działającej aplikacji](../cross-platform/media/xamarin-getstarted-results-windows.png "Xamarin_GetStarted_Results_Windows")

> [!TIP]
> Trwa pełnego kodu źródłowego dla tego projektu [mobile-samples repository w witrynie GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).

## <a name="next"></a> Następne kroki
 **Dodawanie interfejsu użytkownika dla systemu iOS w rozwiązaniu**

 W tym przykładzie należy rozszerzyć przez dodanie natywnego interfejsu użytkownika dla systemu iOS. W tym należy połączyć się z komputerem Mac w sieci lokalnej, która ma Xcode i Xamarin zainstalowane. Po wykonaniu tej czynności można użyć narzędzia iOS designer bezpośrednio w programie Visual Studio. Zobacz [mobile-samples repository w witrynie GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather) dla ukończonej aplikacji.

 Również dotyczyć [Witaj, iOS](/xamarin/ios/get-started/hello-ios/hello-ios-quickstart?pivots=windows) Instruktaż (strony xamarin.com). Należy zauważyć, że na tej stronie można się, że "Visual Studio" jest zaznaczona w w prawym górnym rogu strony na strony xamarin.com i poprawny zestaw instrukcji.

 **Dodawanie kodu specyficznego dla platformy w projekcie udostępnionym**

 Udostępnionego kodu w aplikacji PCL jest niezależny od platformy, ponieważ kompilacji raz i zawarte w każdy pakiet specyficzne dla platformy aplikacji PCL. Jeśli chcesz napisać kod udostępniony, który używa kompilacji warunkowej do izolowania kodu specyficznego dla platformy, możesz użyć *udostępnionego* projektu. Aby uzyskać więcej informacji, zobacz [opcje udostępniania kodu](/xamarin/cross-platform/app-fundamentals/code-sharing) (strony xamarin.com).

## <a name="see-also"></a>Zobacz też
 [Witryna firmy Xamarin dla deweloperów](/xamarin/) [Centrum deweloperów Windows](https://dev.windows.com/en-us) [Swift i C# szybkiego plakatu odwołania](https://aka.ms/scposter)
