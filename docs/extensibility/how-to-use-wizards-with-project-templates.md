---
title: 'Porady: korzystanie z kreatora z szablonami projektu'
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d2dc057dfa518bb52c6ba4d30cd0f3e0a822cfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710543"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Jak: Używanie kreatorów z szablonami projektów

Visual Studio <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> udostępnia interfejs, który po zaimplementacji umożliwia uruchamianie kodu niestandardowego, gdy użytkownik tworzy projekt z szablonu.

Dostosowanie szablonu projektu może służyć do wyświetlania niestandardowego interfejsu użytkownika, który zbiera dane wejściowe użytkownika w celu dostosowania szablonu, dodania dodatkowych plików do szablonu lub dowolnej innej akcji dozwolonej w projekcie.

Metody <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejsu są wywoływane w różnych momentach podczas tworzenia projektu, począwszy od kliknięcia **przycisku OK** w oknie dialogowym **Nowy projekt.** Każda metoda interfejsu jest nazwany do opisania punktu, w którym jest wywoływana. Na przykład Visual <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> Studio wywołuje natychmiast po uruchomieniu tworzenia projektu, dzięki czemu jest to dobra lokalizacja do pisania kodu niestandardowego do zbierania danych wejściowych użytkownika.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Tworzenie projektu szablonu projektu za pomocą projektu VSIX

Rozpoczęcie tworzenia szablonu niestandardowego z projektu szablonu projektu, który jest częścią visual studio SDK. W tej procedurze użyjemy projektu szablonu projektu języka C#, ale istnieje również projekt szablonu projektu języka Visual Basic. Następnie należy dodać projekt VSIX do rozwiązania, które zawiera projekt szablonu projektu.

1. Utwórz projekt szablonu projektu w języku C# (w programie Visual Studio wybierz **pozycję Plik** > **nowego** > **projektu** i wyszukaj "szablon projektu" **Nazwij myprojectTemplate**.

   > [!NOTE]
   > Może zostać poproszony o zainstalowanie pakietu SDK programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

2. Dodaj nowy projekt VSIX w tym samym rozwiązaniu co projekt szablonu projektu (w **Eksploratorze rozwiązań**wybierz węzeł rozwiązania, kliknij prawym przyciskiem myszy i wybierz pozycję **Dodaj** > **nowy projekt** i wyszukaj "vsix"). Nazwij go **MyProjectWizard.**

3. Ustaw projekt VSIX jako projekt startowy. W **Eksploratorze rozwiązań**wybierz węzeł projektu VSIX, kliknij prawym przyciskiem myszy i wybierz polecenie **Ustaw jako projekt startowy**.

4. Dodaj projekt szablonu jako zasób projektu VSIX. W **Eksploratorze rozwiązań**w węźle projektu VSIX znajdź plik *source.extension.vsixmanifest.* Kliknij go dwukrotnie, aby otworzyć go w edytorze manifestów.

5. W edytorze manifestów wybierz kartę **Zasoby** po lewej stronie okna.

6. Na karcie **Zasoby** wybierz pozycję **Nowy**. W oknie **Dodawanie nowego zasobu** dla pola Typ wybierz pozycję **Microsoft.VisualStudio.ProjectTemplate**. W polu **Źródło** wybierz pozycję **Projekt w bieżącym rozwiązaniu**. W polu **Projekt** wybierz pozycję **MyProjectTemplate**. Następnie kliknij przycisk **OK**.

7. Skompiluj rozwiązanie i rozpocznij debugowanie. Pojawi się drugie wystąpienie programu Visual Studio. (Może to potrwać kilka minut).)

8. W drugim wystąpieniu programu Visual Studio spróbuj utworzyć nowy projekt z nowym szablonem (**File** > **New** > **Project**, wyszukaj hasło "myproject"). Nowy projekt powinien pojawić się z klasą o nazwie **Class1**. Teraz utworzono niestandardowy szablon projektu! Zatrzymaj debugowanie teraz.

## <a name="create-a-custom-template-wizard"></a>Tworzenie kreatora szablonów niestandardowych

W tej procedurze pokazano, jak utworzyć niestandardowego kreatora, który otwiera formularz systemu Windows przed utworzeniem projektu. Formularz umożliwia użytkownikom dodawanie wartości parametru niestandardowego, który jest dodawany do kodu źródłowego podczas tworzenia projektu.

1. Skonfiguruj projekt VSIX, aby umożliwić mu utworzenie zestawu.

2. W **Eksploratorze rozwiązań**wybierz węzeł projektu VSIX. Poniżej **Eksplorator rozwiązań**powinien zostać wyświetlony okno **Właściwości.** Jeśli nie, wybierz opcję **Wyświetl** > **okno właściwości**lub naciśnij klawisz **F4**. W oknie **Właściwości** wybierz następujące pola, aby `true`:

   - **Uwzględnij montaż w kontenerze VSIX**

   - **Uwzględnij symbole debugowania w kontenerze VSIX**

   - **Uwzględnij symbole debugowania w lokalnym wdrożeniu VSIX**

3. Dodaj zestaw jako zasób do projektu VSIX. Otwórz plik *source.extension.vsixmanifest* i wybierz kartę **Zasoby.** W oknie **Dodawanie nowego zasobu** dla **opcji Typ** wybierz **pozycję Microsoft.VisualStudio.Assembly**, for **Source** select A project in **current solution**( **Project** select **MyProjectWizard**).

4. Dodaj następujące odwołania do projektu VSIX. (W **Eksploratorze rozwiązań**w węźle projektu VSIX wybierz pozycję **Odwołania**, kliknij prawym przyciskiem myszy i wybierz polecenie **Dodaj odwołanie).** W oknie dialogowym **Dodawanie odwołania** na karcie **Framework** znajdź zestaw **System.Windows Forms** i wybierz go. Znajdź i wybierz również zestawy **System** i **System.Drawing.** Teraz wybierz kartę **Rozszerzenia.** Znajdź zespół **EnvDTE** i wybierz go. Również znaleźć **microsoft.VisualStudio.TemplateWizardInterface** zestawu i wybierz go. Kliknij przycisk **OK**.

5. Dodaj klasę implementacji kreatora do projektu VSIX. (W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu VSIX i wybierz polecenie **Dodaj**, a następnie **pozycję Nowy element**, a następnie **klasę**.) Nazwij klasę **WizardImplementation**.

6. Zastąp kod w pliku *WizardImplementationClass.cs* następującym kodem:

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.TemplateWizard;
   using System.Windows.Forms;
   using EnvDTE;

   namespace MyProjectWizard
   {
       public class WizardImplementation:IWizard
       {
           private UserInputForm inputForm;
           private string customMessage;

           // This method is called before opening any item that
           // has the OpenInEditor attribute.
           public void BeforeOpeningFile(ProjectItem projectItem)
           {
           }

           public void ProjectFinishedGenerating(Project project)
           {
           }

           // This method is only called for item templates,
           // not for project templates.
           public void ProjectItemFinishedGenerating(ProjectItem
               projectItem)
           {
           }

           // This method is called after the project is created.
           public void RunFinished()
           {
           }

           public void RunStarted(object automationObject,
               Dictionary<string, string> replacementsDictionary,
               WizardRunKind runKind, object[] customParams)
           {
               try
               {
                   // Display a form to the user. The form collects
                   // input for the custom message.
                   inputForm = new UserInputForm();
                   inputForm.ShowDialog();

                   customMessage = UserInputForm.CustomMessage;

                   // Add custom parameters.
                   replacementsDictionary.Add("$custommessage$",
                       customMessage);
               }
               catch (Exception ex)
               {
                   MessageBox.Show(ex.ToString());
               }
           }

           // This method is only called for item templates,
           // not for project templates.
           public bool ShouldAddProjectItem(string filePath)
           {
               return true;
           }
       }
   }
   ```

    **UserInputForm,** do którego odwołuje się ten kod zostaną zaimplementowane później.

    Klasa `WizardImplementation` zawiera implementacje metody <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>dla każdego członka . W tym przykładzie <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> tylko metoda wykonuje zadanie. Wszystkie inne metody albo nic `true`nie robić lub powrót .

    Metoda <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> akceptuje cztery parametry:

   - Parametr, <xref:System.Object> który może być <xref:EnvDTE._DTE> rzutowanie do obiektu głównego, aby umożliwić dostosowanie projektu.

   - Parametr, <xref:System.Collections.Generic.Dictionary%602> który zawiera kolekcję wszystkich wstępnie zdefiniowanych parametrów w szablonie. Aby uzyskać więcej informacji na temat parametrów [szablonu,](../ide/template-parameters.md)zobacz Parametry szablonu .

   - Parametr, <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> który zawiera informacje o rodzaju szablonu jest używany.

   - Tablica <xref:System.Object> zawierająca zestaw parametrów przekazanych do kreatora przez program Visual Studio.

     W tym przykładzie dodaje wartość parametru <xref:System.Collections.Generic.Dictionary%602> z formularza wejściowego użytkownika do parametru. Każde wystąpienie `$custommessage$` parametru w projekcie zostanie zastąpione tekstem wprowadzonym przez użytkownika.

7. Teraz utwórz **userinputForm**. W pliku *WizardImplementation.cs* dodaj następujący kod po zakończeniu `WizardImplementation` klasy.

   ```csharp
   public partial class UserInputForm : Form
       {
           private static string customMessage;
           private TextBox textBox1;
           private Button button1;

           public UserInputForm()
           {
               this.Size = new System.Drawing.Size(155, 265);

               button1 = new Button();
               button1.Location = new System.Drawing.Point(90, 25);
               button1.Size = new System.Drawing.Size(50, 25);
               button1.Click += button1_Click;
               this.Controls.Add(button1);

               textBox1 = new TextBox();
               textBox1.Location = new System.Drawing.Point(10, 25);
               textBox1.Size = new System.Drawing.Size(70, 20);
               this.Controls.Add(textBox1);
           }
           public static string CustomMessage
           {
               get
               {
                   return customMessage;
               }
               set
               {
                   customMessage = value;
               }
           }
           private void button1_Click(object sender, EventArgs e)
           {
               customMessage = textBox1.Text;
               this.Close();
           }
       }
   ```

    Formularz wprowadzania danych użytkownika zawiera prosty formularz do wprowadzania parametru niestandardowego. Formularz zawiera pole tekstowe o `textBox1` `button1`nazwie i przycisk o nazwie . Po kliknięciu przycisku tekst z pola tekstowego `customMessage` jest przechowywany w parametrze.

## <a name="connect-the-wizard-to-the-custom-template"></a>Łączenie kreatora z szablonem niestandardowym

Aby niestandardowy szablon projektu używał niestandardowego kreatora, musisz podpisać zestaw kreatora i dodać kilka wierszy do niestandardowego szablonu projektu, aby poinformować go, gdzie można znaleźć implementację kreatora podczas tworzenia nowego projektu.

1. Podpisz zespół. W **Eksploratorze rozwiązań**wybierz projekt VSIX, kliknij prawym przyciskiem myszy i wybierz polecenie **Właściwości projektu**.

2. W oknie **Właściwości projektu** wybierz kartę **Podpisywanie** na karcie **Podpisywanie,** zaznacz pozycję **Podpisz zestaw**. W polu **Wybierz plik klucza silnej nazwy** wybierz pozycję ** \<Nowy>**. W oknie **Utwórz klucz silnej nazwy** w polu **Nazwa pliku klucza** wpisz **plik key.snk**. Wyeznacz pole **Chroń mój plik klucza za pomocą** pola hasła.

3. W **Eksploratorze rozwiązań**wybierz projekt VSIX i znajdź okno **Właściwości.**

4. Ustaw pole **Kopiuj dane wyjściowe kompilacji na katalog wyjściowy** na **true**. Dzięki temu zestaw do skopiowania do katalogu wyjściowego, gdy rozwiązanie jest przebudowywany. Nadal jest zawarty w `.vsix` pliku. Musisz zobaczyć zestaw, aby dowiedzieć się jego klucz podpisywania.

5. Ponownie skompiluj rozwiązanie.

6. Plik key.snk można teraz znaleźć w katalogu projektu MyProjectWizard*\<(lokalizacja dysku>\MyProjectTemplate\MyProjectWizard\key.snk*). Skopiuj plik *key.snk.*

7. Przejdź do katalogu wyjściowego i znajdź zestaw*\<(lokalizacja dysku>\MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll*). Wklej plik *key.snk* tutaj. (Nie jest to absolutnie konieczne, ale ułatwi następujące kroki).

8. Otwórz okno polecenia i zmień katalog, w którym utworzono zestaw.

9. Znajdź narzędzie do podpisywania *sn.exe.* Na przykład w 64-bitowym systemie operacyjnym Windows 10 typowa ścieżka będzie następująca:

     *C:\Pliki programów (x86)\Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Narzędzia*

     Jeśli nie możesz znaleźć narzędzia, spróbuj uruchomić **miejsce, w którym plik /R . sn.exe** w oknie polecenia. Zanotuj ścieżkę.

10. Wyodrębnij klucz publiczny z pliku *key.snk.* W oknie polecenia wpisz

     **\<lokalizacja sn.exe>\sn.exe -p key.snk outfile.key.**

     Nie zapomnij otoczyć ścieżkę *sn.exe* cudzysłowami, jeśli w nazwach katalogów znajdują się spacje!

11. Pobierz token klucza publicznego z pliku outfile:

     **\<lokalizacja sn.exe>\sn.exe -t outfile.key.**

     Ponownie, nie zapomnij o cudzysłowach. Powinieneś zobaczyć linię na wyjściu w ten sposób

     **Token klucza \<publicznego jest tokenem>**

     Zanotuj tę wartość.

12. Dodaj odwołanie do kreatora niestandardowego do pliku *vstemplate* szablonu projektu. W **Eksploratorze rozwiązań**znajdź plik o nazwie *MyProjectTemplate.vstemplate*i otwórz go. Po zakończeniu sekcji \<TemplateContent> dodaj następującą sekcję:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Gdzie **MyProjectWizard** jest nazwą zestawu, a **token** jest token skopiowany w poprzednim kroku.

13. Zapisz wszystkie pliki w projekcie i odbuduj.

## <a name="add-the-custom-parameter-to-the-template"></a>Dodawanie parametru niestandardowego do szablonu

W tym przykładzie projekt używany jako szablon wyświetla komunikat określony w formularzu wprowadzania danych użytkownika kreatora niestandardowego.

1. W **Eksploratorze rozwiązań**przejdź do projektu **MyProjectTemplate** i otwórz *Class1.cs*.

2. W `Main` metodzie aplikacji dodaj następujący wiersz kodu.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    Parametr `$custommessage$` jest zastępowany tekstem wprowadzonym w formularzu wprowadzania użytkownika podczas tworzenia projektu na podstawie szablonu.

Oto pełny plik kodu, zanim został wyeksportowany do szablonu.

```csharp
using System;
using System.Collections.Generic;
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;
$endif$using System.Text;

namespace $safeprojectname$
{
    public class Class1
    {
          static void Main(string[] args)
          {
               Console.WriteLine("$custommessage$");
          }
    }
}
```

## <a name="use-the-custom-wizard"></a>Korzystanie z kreatora niestandardowego

Teraz możesz utworzyć projekt z szablonu i użyć kreatora niestandardowego.

1. Odbuduj rozwiązanie i rozpocznij debugowanie. Powinno pojawić się drugie wystąpienie programu Visual Studio.

2. Utwórz nowy projekt MyProjectTemplate. **(Plik** > **nowego** > **projektu**).

3. W oknie dialogowym **Nowy projekt** wyszukaj hasło "mój projekt", aby zlokalizować szablon, wpisz nazwę i kliknij przycisk **OK**.

     Zostanie otwarty formularz wprowadzania użytkownika kreatora.

4. Wpisz wartość parametru niestandardowego i kliknij przycisk.

     Formularz wprowadzania użytkownika kreatora zostanie zamknięty, a projekt zostanie utworzony na podstawie szablonu.

5. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy plik kodu źródłowego i kliknij polecenie **Wyświetl kod**.

     Należy `$custommessage$` zauważyć, że został zastąpiony tekstem wprowadzonym w formularzu wprowadzania użytkownika kreatora.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Element WizardExtension (szablony programu Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Pakiety NuGet w szablonach programu Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
