---
title: 'Instrukcje: Korzystanie z kreatorów z szablonami projektu'
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4ff83c2d4d28b6393f7f6d03b01e35d9cc0aa4f
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58324644"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Instrukcje: Korzystanie z kreatorów z szablonami projektu

Program Visual Studio udostępnia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejs, który, po wdrożeniu, umożliwia uruchamianie kodu niestandardowego, gdy użytkownik tworzy projekt z szablonu.

Dostosowywanie szablonu projektu może służyć do wyświetlania niestandardowego interfejsu użytkownika, który zbiera dane wejściowe, aby dostosować szablon, Dodaj dodatkowe pliki do szablonu użytkownika lub dowolne akcje dozwolone w projekcie.

<xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Metody interfejsu nazywane są w różnym czasie, gdy projekt jest tworzony, od początku tak szybko, jak użytkownik kliknie **OK** na **nowy projekt** okno dialogowe. Każda metoda interfejsu nosi nazwę aby opisać punkt w którym jest wywoływana. Na przykład programu Visual Studio wywołuje <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> natychmiast po rozpoczęciu do tworzenia projektu, dzięki czemu jest dobrym miejscem do napisania kodu niestandardowego, aby zbierać dane wejściowe użytkownika.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Utwórz projekt szablonu projektu z projektu VSIX

Możesz rozpocząć tworzenie szablonu niestandardowego za pomocą projektu szablonu projektu, który jest częścią zestawu SDK programu Visual Studio. W tej procedurze użyto C# projektu szablonu projektu, ale jest również szablon projektami Visual Basic. Następnie możesz dodać projekt VSIX do rozwiązania zawierającego projekt szablonu projektu.

1. Tworzenie C# szablonu projektu (w programie Visual Studio, wybierz **pliku** > **New** > **projektu** i poszukaj pozycji "szablon projektu" ). Nadaj mu nazwę **MyProjectTemplate**.

   > [!NOTE]
   > Może być konieczne instalowanie zestawu SDK programu Visual Studio. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

2. Dodaj nowy projekt VSIX w tym samym rozwiązaniu co projekt szablonu projektu (w **Eksploratora rozwiązań**, wybierz węzeł rozwiązania, kliknij prawym przyciskiem myszy i wybierz **Dodaj** > **nowy projekt**  i poszukaj pozycji "vsix"). Nadaj mu nazwę **MyProjectWizard.**

3. Ustaw projekt VSIX jako projekt startowy. W **Eksploratora rozwiązań**, wybierz węzeł projektu VSIX, kliknij prawym przyciskiem myszy i wybierz **Ustaw jako projekt startowy**.

4. Dodaj szablon projektu jako zasób usługi w projekcie VSIX. W **Eksploratora rozwiązań**, w obszarze węzła projektu VSIX, Znajdź *source.extension.vsixmanifest* pliku. Kliknij dwukrotnie, aby go otworzyć w edytorze manifestu.

5. W edytorze manifestu, wybierz **zasoby** karty w lewej części okna.

6. W **zasoby** zaznacz **New**. W **Dodaj nowy zasób** okna dla pól typu, zaznacz **Microsoft.VisualStudio.ProjectTemplate**. W **źródła** pól, zaznacz **projekt w bieżącym rozwiązaniu**. W **projektu** pól, zaznacz **MyProjectTemplate**. Następnie kliknij przycisk **OK**.

7. Skompiluj rozwiązanie, a następnie rozpocząć debugowanie. Zostanie wyświetlone drugie wystąpienie programu Visual Studio. (Może to potrwać kilka minut).

8. W drugim wystąpieniu programu Visual Studio, spróbuj utworzyć nowy projekt za pomocą nowego szablonu (**pliku** > **New** > **projektu**, wyszukaj " myProject"). Nowy projekt powinno zostać wyświetlone klasę o nazwie **klasa1**. Utworzono szablonu niestandardowego projektu! Zatrzymać debugowanie.

## <a name="create-a-custom-template-wizard"></a>Tworzenie kreatora niestandardowego szablonu

Poniższa procedura przedstawia sposób tworzenia niestandardowego kreatora, który służy do otwierania formularza Windows przed utworzeniem projektu. Formularz pozwala użytkownikom na dodawanie wartości parametru niestandardowego, który jest dodawany do kodu źródłowego podczas tworzenia projektu.

1. Konfigurowanie projektu VSIX, aby zezwalała na utworzenie zestawu.

2. W **Eksploratora rozwiązań**, wybierz węzeł projektu VSIX. Poniżej **Eksploratora rozwiązań**, powinien zostać wyświetlony **właściwości** okna. Jeśli tego nie zrobisz, wybierz opcję **widoku** > **okno właściwości**, lub naciśnij **F4**. W **właściwości** okna, wybierz następujące pola do `true`:

   - **IncludeAssemblyInVSIXContainer**

   - **IncludeDebugSymbolsInVSIXContainer**

   - **IncludeDebugSymbolsInLocalVSIXDeployment**

3. Dodaj zestaw jako zasobu w projekcie VSIX. Otwórz *source.extension.vsixmanifest* plik i wybierz **zasoby** kartę. W **Dodaj nowy zasób** oknie dla **typu** wybierz **Microsoft.VisualStudio.Assembly**, dla **źródła** wybierz **A Projekt w bieżącym rozwiązaniu**oraz **projektu** wybierz **MyProjectWizard**.

4. Dodaj następujące odwołania do projektu VSIX. (W **Eksploratora rozwiązań**, w węźle projektu VSIX wybierz **odwołania**, kliknij prawym przyciskiem myszy, a następnie wybierz **Dodaj odwołanie**.) W **Dodaj odwołanie** okna dialogowego w **Framework** kartę, Znajdź **formularzy System.Windows** zestawu i wybierz ją. Teraz wybierz **rozszerzenia** kartę. Znajdź **EnvDTE** zestawu i wybierz ją. Również znaleźć **Microsoft.VisualStudio.TemplateWizardInterface** zestawu i wybierz ją. Kliknij przycisk **OK**.

5. Dodaj klasę dla Kreatora wdrażania w projekcie VSIX. (W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu VSIX i wybierz **Dodaj**, następnie **nowy element**, następnie **klasy**.) Nazwa klasy **WizardImplementation**.

6. Zastąp kod w *WizardImplementationClass.cs* pliku następującym kodem:

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

    **UserInputForm** do którego odwołuje się ten kod będzie wykonywane później.

    `WizardImplementation` Klasa zawiera implementacje metod dla każdego członka <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>. W tym przykładzie, tylko <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> metoda wykonuje zadanie. Wszystkie inne metody nic nie rób lub zwrócić `true`.

    <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> Metoda przyjmuje cztery parametry:

   - <xref:System.Object> Parametr, który może być rzutowany w katalogu głównym <xref:EnvDTE._DTE> obiektu, aby umożliwić dostosować projekt.

   - A <xref:System.Collections.Generic.Dictionary%602> parametr, który zawiera zbiór wszystkich parametrów wstępnie zdefiniowanych w szablonie. Aby uzyskać więcej informacji na temat parametrów szablonu, zobacz [parametry szablonu](../ide/template-parameters.md).

   - A <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> parametr, który zawiera informacje o jakiego typu szablon jest używany.

   - <xref:System.Object> Tablicę, która zawiera zestaw parametrów przekazanych do kreatora przez program Visual Studio.

     Ten przykład dodaje wartości parametru z formularza wejściowego użytkownika do <xref:System.Collections.Generic.Dictionary%602> parametru. Każde wystąpienie `$custommessage$` parametru w projekcie zostanie zastąpione tekstem wprowadzonym przez użytkownika. Dodaj następujące zestawy do projektu: **System** i **System.Drawing**.

7. Teraz Utwórz **UserInputForm**. W *WizardImplementation.cs* plików, Dodaj następujący kod na końcu `WizardImplementation` klasy.

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

    Formularz wprowadzania użytkownika zapewnia prosty formularz Wprowadzanie parametru niestandardowego. Formularz zawiera pole tekstowe o nazwie `textBox1` i przycisk o nazwie `button1`. Po kliknięciu przycisku, tekst z pola tekstowego jest przechowywany w `customMessage` parametru.

## <a name="connect-the-wizard-to-the-custom-template"></a>Kreator nawiązać połączenie z szablonu niestandardowego

Szablon niestandardowy projekt, aby użyć niestandardowego kreatora, musisz podpisać zestaw kreatora i dodaj kilka wierszy do szablonu niestandardowego projektu o tym, gdzie można znaleźć implementacji kreatora podczas tworzenia nowego projektu.

1. Podpisz zestaw. W **Eksploratora rozwiązań**, wybierz projekt VSIX, kliknij prawym przyciskiem myszy i wybierz **właściwości projektu**.

2. W **właściwości projektu** wybierz **podpisywanie** kartę w **podpisywanie** karcie wyboru **Podpisz zestaw**. W **wybierz plik klucza o silnej nazwie** pól, zaznacz  **\<nowy >**. W **Utwórz klucz silnej nazwy** okna w **nazwę pliku klucza** wpisz **key.snk**. Usuń zaznaczenie pola wyboru **Chroń mój plik klucza przy użyciu hasła** pola.

3. W **Eksploratora rozwiązań**, wybierz projekt VSIX i Znajdź **właściwości** okna.

4. Ustaw **katalog danych wyjściowych danych wyjściowych kompilacji kopiowania** pole **true**. Dzięki temu zestaw, który ma być skopiowany do katalogu wyjściowego, gdy rozwiązanie zostanie ponownie skompilowany. Nadal znajduje się w `.vsix` pliku. Zachodzi potrzeba wyświetlenia zestawu, aby dowiedzieć się, jego klucza podpisywania.

5. Ponownie skompiluj rozwiązanie.

6. Teraz można znaleźć pliku key.snk w katalogu projektu MyProjectWizard (*\<lokalizacji na dysku > \MyProjectTemplate\MyProjectWizard\key.snk*). Kopiuj *key.snk* pliku.

7. Przejdź do katalogu wyjściowego i Znajdź zestaw (*\<lokalizacji na dysku > \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll*). Wklej *key.snk* pliku w tym miejscu. (Nie jest to absolutnie konieczne, ale jej ułatwi następujące kroki).

8. Otwórz okno polecenia i przejdź do katalogu, w którym utworzono zestaw.

9. Znajdź *sn.exe* narzędzia podpisywania. Na przykład w systemie operacyjnym 64-bitowego systemu Windows 10, typowe ścieżki będzie następujące:

     *C:\Program Files (x86)\Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Tools*

     Jeśli nie można odnaleźć narzędzia, spróbuj uruchomić **gdzie /R. sn.exe** w oknie wiersza polecenia. Zanotuj ścieżkę.

10. Wyodrębnij klucz publiczny z *key.snk* pliku. W oknie wiersza polecenia wpisz:

     **\<Lokalizacja sn.exe > \sn.exe -p key.snk outfile.key.**

     Nie zapomnij Otocz ścieżkę *sn.exe* w znaki cudzysłowu, jeśli istnieją spacje w nazwach katalogów!

11. Pobierz token klucza publicznego z PlikWyjściowy:

     **\<Lokalizacja sn.exe > outfile.key -t \sn.exe.**

     Ponownie nie zapomnij znaki cudzysłowu. Powinien zostać wyświetlony wiersz w danych wyjściowych, takich jak to

     **Token klucza publicznego jest \<tokenu >**

     Zanotuj tę wartość.

12. Dodawanie odwołania do niestandardowego kreatora, aby *.vstemplate* pliku szablonu projektu. W **Eksploratora rozwiązań**, Znajdź plik o nazwie *MyProjectTemplate.vstemplate*, a następnie otwórz go. Po zakończeniu \<TemplateContent > sekcji, dodaj następującą sekcję:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Gdzie **MyProjectWizard** to nazwa zestawu, a **tokenu** jest token został skopiowany w poprzednim kroku.

13. Zapisz wszystkie pliki w projekcie i ponownie skompilować.

## <a name="add-the-custom-parameter-to-the-template"></a>Dodawanie parametru niestandardowego do szablonu

W tym przykładzie projekt użyty jako szablonu nie wyświetla komunikat określony w postaci danych wejściowych użytkownika niestandardowego kreatora.

1. W **Eksploratora rozwiązań**, przejdź do **MyProjectTemplate** projektu, a następnie otwórz *Class1.cs*.

2. W `Main` metoda aplikacji, Dodaj następujący wiersz kodu.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    Parametr `$custommessage$` zostaje zastąpiony tekstem wprowadzonym w formularzu wejściowym użytkownika, gdy projekt jest tworzony na podstawie tego szablonu.

Oto pełny kod pliku zanim został on wyeksportowany do szablonu.

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

## <a name="use-the-custom-wizard"></a>Użyć niestandardowego kreatora

Teraz możesz utworzyć projekt na podstawie szablonu i użyć niestandardowego kreatora.

1. Ponownie skompiluj rozwiązanie, a następnie rozpocząć debugowanie. Drugie wystąpienie programu Visual Studio powinny być wyświetlane.

2. Utwórz nowy projekt MyProjectTemplate. (**Pliku** > **nowe** > **projektu**).

3. W **nowy projekt** okno dialogowe, wyszukaj "myproject" zlokalizuj szablon, wpisz nazwę, a następnie kliknij przycisk **OK**.

     Zostanie otwarty formularz wprowadzania użytkownika kreatora.

4. Wpisz wartość dla parametru niestandardowego, a następnie kliknij przycisk.

     Formularz wprowadzania użytkownika kreatora zostanie zamknięty, a projekt jest tworzony na podstawie tego szablonu.

5. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik kodu źródłowego i kliknij przycisk **Wyświetl kod**.

     Należy zauważyć, że `$custommessage$` został zastąpiony tekstem wprowadzonym w formularz wprowadzania użytkownika kreatora.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Wizardextension — element (szablony Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Pakiety NuGet w szablonach programu Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)