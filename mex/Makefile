.PHONY:clean
.PHONY:check
.PHONY:style

redis_.mex: redis_.c
	mkoctfile -Wall -Wextra -v -I/usr/include/hiredis --mex $< -lhiredis

style:
	astyle --style=gnu -s2 redis_.c

check: redis_.mex
	octave -f -q --no-gui --eval 'test_redis, disp("----------"), test_redis'
	octave -f -q --no-gui --eval 'redis_("PING"), redis_("keys *"), redis_ ("PING")'

clean:
	rm -f *.o redis_.mex
