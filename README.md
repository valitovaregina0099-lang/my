import org.openjdk.jmh.annotations.*;

import java.util.concurrent.TimeUnit;

@BenchmarkMode(Mode.AverageTime)
@OutputTimeUnit(TimeUnit.MILLISECONDS)
@State(Scope.Benchmark)   // теперь корректно
public class StringConcatBenchmark {

    @Benchmark
    public String testStringConcat() {
        String result = "";
        for (int i = 0; i < 1000; i++) result += i;
        return result;
    }

    @Benchmark
    public String testStringBuilder() {
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < 1000; i++) sb.append(i);
        return sb.toString();
    }
}

// Отдельный класс:
public class BenchmarkRunner {
    public static void main(String[] args) throws Exception {
        org.openjdk.jmh.Main.main(args);
    }
}
