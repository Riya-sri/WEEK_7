class Main
{
    public static int f(int r, int b, int g, char prev)
    {
        // base case: invalid number of balls
        if (r < 0 || b < 0 || g < 0) {
            return 0;
        }
        if (r == 0 && b == 0 && g == 0) {
            return 1;
        }
        if (prev == 'r')
        {
            return f(r, b - 1, g, 'b') + f(r, b, g - 1, 'g');
        }

        if (prev == 'b')
        {
            return f(r - 1, b, g, 'r') + f(r, b, g - 1, 'g');
        }
 
        if (prev == 'g')
        {
            return f(r - 1, b, g, 'r') + f(r, b - 1, g, 'b');
        }
 
        return 0;
    }
    public static int totalWays(int r, int b, int g)
    {
        return f(r - 1, b, g, 'r') +
                f(r, b - 1, g, 'b') +
                f(r, b, g - 1, 'g');
    }
 
    public static void main(String[] args)
    {
        int r = 2, b = 3, g = 1;
        System.out.println("The total number of distinct arrangements are "
                        + totalWays(r, b, g));
    }
}
