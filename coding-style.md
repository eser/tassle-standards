C# Coding Style
===============

The general rule we follow is "use Visual Studio defaults" with some modifications.

1. We use [Stroustrup style](http://en.wikipedia.org/wiki/Indent_style#Stroustrup) braces, where each brace begins on the same line in most cases.
2. We use four spaces of indentation (no tabs).
3. We use `camelCase` for private, protected, protected internal fields. We don't use any prefix for instance, static or thread static field naming.
4. We use `PascalCase` for internal and public members, namespace names, type names, constants, enum values, properties, events and methods.
5. We use `camelCase` for parameter and variable names.
6. We use `readonly` where possible. When used on static fields, `readonly` should come after `static` (i.e. `static readonly` not `readonly static`).
7. We prefer `this.` as much as possible.
8. We always specify the visibility, even if it's the default (i.e.
   `private string foo` not `string foo`). Visibility should be the first modifier (i.e. 
   `public abstract` not `abstract public`).
9. Async methods must be suffixed with 'Async'.
10. Namespace imports should be specified at the top of the file, *outside* of
   `namespace` declarations and should be sorted alphabetically.
11. Avoid more than one empty line at any time. For example, do not have two
   blank lines between members of a type.
12. Avoid spurious free spaces.
   For example avoid `if (someVar == 0)...`, where the dots mark the spurious free spaces.
   Consider enabling "View White Space (Ctrl+E, S)" if using Visual Studio, to aid detection.
13. We only use `var` when it's obvious what the variable type is (i.e. `var stream = new FileStream(...)` not `var stream = OpenStandardInput()`).
14. We use language keywords instead of BCL types (i.e. `int, string, float` instead of `Int32, String, Single`, etc) for both type references as well as method calls (i.e. `int.Parse` instead of `Int32.Parse`).
15. We use ```nameof(...)``` instead of ```"..."``` whenever possible and relevant.
16. Fields should be specified at the top within type declarations.
17. When including non-ASCII characters in the source code use Unicode escape sequences (\uXXXX) instead of literal characters. Literal non-ASCII characters occasionally get garbled by a tool or editor.
18. We encourage early return usage as much as possible.
19. We use [Code Contracts](https://docs.microsoft.com/en-us/dotnet/framework/debug-trace-profile/code-contracts) to check preconditions, postconditions, and object invariants in a code block.
20. We prefer [string interpolation](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/tokens/interpolated) over concatination of strings with '+' operator.


### Example File:

``ObservableLinkedList{T}.cs:``

```C#
using System;
using System.Collections;
using System.Collections.Generic;
using System.Collections.Specialized;
using System.ComponentModel;
using System.Diagnostics;
using Microsoft.Win32;

namespace System.Collections.Generic {
    public partial class ObservableLinkedList<T> : INotifyCollectionChanged, INotifyPropertyChanged {
        private ObservableLinkedListNode<T> head;
        private int count;

        public ObservableLinkedList(IEnumerable<T> items) {
            if (items == null) {
                throw new ArgumentNullException(nameof(items));
            }

            foreach (T item in items) {
                this.AddLast(item);
            }
        }

        public event NotifyCollectionChangedEventHandler CollectionChanged;

        public int Count {
            get { return this.count; }
        }

        public ObservableLinkedListNode AddLast(T value) {
            var newNode = new LinkedListNode<T>(this, value);

            this.InsertNodeBefore(this.head, node);
        }

        protected virtual void OnCollectionChanged(NotifyCollectionChangedEventArgs e) {
            NotifyCollectionChangedEventHandler handler = this.CollectionChanged;

            if (handler != null) {
                handler(this, e);
                return;
            }

            Debug.Write("no handlers for collection change event");
        }

        private void InsertNodeBefore(LinkedListNode<T> node, LinkedListNode<T> newNode) {
           ...
        }
        
        ...
    }
}
```

``ObservableLinkedList{T}.ObservableLinkedListNode.cs:``

```C#
using System;

namespace System.Collections.Generics {
    partial class ObservableLinkedList<T> {
        public class ObservableLinkedListNode {
            private readonly ObservableLinkedList<T> parent;
            private readonly T value;

            internal ObservableLinkedListNode(ObservableLinkedList<T> parent, T value) {
                Debug.Assert(parent != null);

                this.parent = parent;
                this.value = value;
            }
            
            public T Value {
               get { return this.value; }
            }
        }

        ...
    }
}
```
