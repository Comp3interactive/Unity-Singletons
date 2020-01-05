# Unity-Singletons
 A collection of write inheritable Singleton scripts for Unity

<b>How to use</b></br>
Simply inherit any of your scripts from either <code>Singleton&lt;T&gt;</code> or <code>SingletonDontDestroy&lt;T&gt;</code> and that script will automatically inherit it's own instance and be made available as a singleton</br></br>
Inheriting from <code>Singleton&lt;T&gt;</code> will simply make the object a singleton whereas inheriting from <code>SingletonDontDestroy&lt;T&gt;</code> will ensure the object persists between scenes by adding it to the DontDestroyOnLoad list.
 
<b>Examples</b></br>
<i>Inheriting from the given classes</i></br>
<pre>
public class ScoreManager : Singleton&lt;ScoreManager&gt;
{
    private int score;
    public void AddScore(int i)
    {
        score += i;
    }
 }
</pre>

<pre>
public class ScoreManager : SingletonDontDestroy&lt;ScoreManager&gt;
{
    private int score;
    public void AddScore(int i)
    {
        score += i;
    }
 }
</pre>

<i>Calling the classes instance from elsewhere in your project</i></br>
<pre>
public class Enemy
{
    private int scoreForKill = 100;
    public void OnKill()
    {
        ScoreManager.instance.AddScore(scoreForKill);
    }
}
</pre>
